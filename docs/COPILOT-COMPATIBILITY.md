# GitHub Copilot compatibility baseline

**Status: documentation baseline complete; client validation blocked.** On
2026-11-20, this environment had no `copilot`, `code`, or `code-insiders`
executable. No client versions, feature settings, or plugin behaviors could be
tested. This is a blocker, not a pass. Do not describe the current Claude
packages as Copilot-verified or publish a version-support claim from this
baseline.

This record separates vendor-documented behavior from behavior that still needs
to be reproduced in isolated profiles. It is a packaging decision input, not a
new installation guide.

## What exists in this repository

- **Canonical source:** 95 folders under `skills/`, each with `SKILL.md`.
  Frontmatter includes `name`, `description`, `intent`, `type`, `theme`,
  `best_for`, `scenarios`, and `estimated_time` on all 95 skills; 91 also have
  `argument-hint`, and 3 have `sources`. Types are 36 Component, 34 Interactive,
  and 25 Workflow. The canonical `SKILL.md` is authoritative for each skill's
  full metadata and teaching content.
- **Supporting resources:** 69 `template.md` files, 132 files under
  `examples/`, and two Python scripts. The scripts are
  `skills/tam-sam-som-calculator/scripts/market-sizing.py` and
  `skills/user-story/scripts/user-story-template.py`. These files are
  co-located with the skill that refers to them.
- **Bundles:** `pm-skills.config.yaml` assigns every skill exactly one home
  across six lifecycle bundles; five Core skills are shared infrastructure.
  `scripts/check-bundles.py` validates the one-home invariant. Existing bundle
  generation copies each selected skill directory in full, including its
  templates, examples, and scripts.
- **References:** skill-to-skill links are references, not declared runtime
  dependencies. A lifecycle bundle contains its own skills plus all five Core
  skills. `scripts/build-plugins.py` keeps relative links to those included
  folders and rewrites other relative Markdown links to GitHub `blob/main`
  URLs in the generated copy. Those remote links require network access and do
  not make the referenced skill available in the installed plugin. A proposed
  all-skills package should include all 95 folders and preserve local links.
- **Commands:** six Markdown workflow wrappers live in `commands/`. They are
  not copied by `scripts/build-plugins.py`; the current bundle manifests do not
  declare a command directory.

The inventory below uses `T` for a template, `E#` for the number of example
files, and `—` for none. “Other-bundle links” lists Markdown skill links whose
target is not in that skill's lifecycle bundle or Core. Those links remain
external under current bundle generation; they are not silently satisfied by
installing that bundle. Same-bundle/Core references are omitted from this
column because those skills are included together.

| Canonical skill | Type | Intended existing component | Local resources | Other-bundle links |
|---|---|---|---|---|
| `acquisition-channel-advisor` | interactive | deliver / demand | E1 | — |
| `activation-design` | component | deliver / deepen | T, E2 | `customer-journey-map`, `usage-data-investigation` |
| `agent-orchestration-advisor` | interactive | develop / delegate | — | `discovery-process`, `pol-probe-advisor` |
| `ai-shaped-readiness-advisor` | interactive | develop / delegate | — | `discovery-process`, `epic-hypothesis`, `pol-probe-advisor`, `positioning-statement`, `problem-statement` |
| `altitude-horizon-framework` | component | drive / demystify | T, E2 | — |
| `ansoff-matrix` | workflow | determine / diagnose | T, E2 | `opportunity-solution-tree` |
| `assumption-mapping` | component | discover / decode | T, E2 | `derisk-measurement-advisor`, `epic-hypothesis`, `lean-ux-canvas`, `pol-probe`, `pol-probe-advisor`, `recommendation-canvas` |
| `autonomous-investigation` | workflow | Core / shared | T, E2 | `intelligence-collection-disciplines` |
| `backlog-refinement-advisor` | interactive | develop / drumbeat | — | — |
| `battle-card-builder` | workflow | define / differentiate | T, E2 | `competitive-intel-watch`, `competitive-research-snapshot`, `intelligence-collection-disciplines` |
| `business-health-diagnostic` | interactive | determine / direct | — | — |
| `buying-journey-enablement` | workflow | deliver / debut | T, E2 | `battle-card-builder`, `customer-journey-map`, `customer-journey-mapping-workshop` |
| `company-intel` | workflow | determine / detect | T, E2 | `acquisition-channel-advisor`, `derisk-measurement-advisor`, `positioning-statement` |
| `company-research` | component | determine / detect | T, E2 | — |
| `competitive-analysis-process` | workflow | determine / detect | T, E2 | `battle-card-builder`, `positioning-statement` |
| `competitive-intel-watch` | workflow | determine / detect | T, E2 | `battle-card-builder` |
| `competitive-research-snapshot` | workflow | determine / detect | T, E2 | `battle-card-builder` |
| `context-engineering-advisor` | interactive | develop / delegate | — | `epic-hypothesis`, `pol-probe-advisor`, `problem-statement` |
| `customer-journey-map` | component | discover / drill-down | T, E2 | — |
| `customer-journey-mapping-workshop` | interactive | discover / drill-down | — | — |
| `decision-rights-matrix` | component | drive / delineate | T, E2 | `eol-readiness-advisor`, `eol-stakeholder-sequence`, `launch-plan`, `prioritization-advisor` |
| `derisk-measurement-advisor` | interactive | define / de-risk | — | `pestel-analysis`, `problem-framing-canvas` |
| `director-readiness-advisor` | interactive | drive / demystify | E1 | — |
| `discovery-habits-advisor` | interactive | discover / dig | — | — |
| `discovery-interview-prep` | interactive | discover / drill-down | — | — |
| `discovery-process` | workflow | discover / drill-down | T, E2 | — |
| `eol-checklist` | component | deliver / decommission | T, E2 | — |
| `eol-internal-enablement` | component | deliver / decommission | T, E2 | `incoming-request-advisor` |
| `eol-message` | component | deliver / decommission | T, E2 | `positioning-statement`, `problem-statement`, `proto-persona` |
| `eol-process` | workflow | deliver / decommission | T, E2 | `positioning-statement`, `stakeholder-mapping` |
| `eol-readiness-advisor` | interactive | deliver / decommission | — | `business-health-diagnostic`, `incoming-request-advisor`, `stakeholder-mapping` |
| `eol-stakeholder-sequence` | component | deliver / decommission | T, E2 | `stakeholder-mapping` |
| `epic-breakdown-advisor` | interactive | develop / draft | — | — |
| `epic-hypothesis` | component | define / de-risk | T, E2 | — |
| `executive-onboarding-playbook` | workflow | drive / demystify | T, E2 | — |
| `feature-investment-advisor` | interactive | determine / direct | E1 | — |
| `finance-based-pricing-advisor` | interactive | deliver / dollars | — | — |
| `finance-metrics-quickref` | component | determine / direct | T | — |
| `incoming-request-advisor` | interactive | drive / diplomacy | T, E1 | `jobs-to-be-done`, `opportunity-solution-tree`, `problem-statement` |
| `intel-discipline-advisor` | interactive | determine / detect | T, E2 | `battle-card-builder`, `discovery-interview-prep`, `positioning-statement`, `pricing-packaging-tracker` |
| `intelligence-collection-disciplines` | component | determine / detect | T, E2 | — |
| `jobs-to-be-done` | component | determine / describe | T, E2 | — |
| `launch-metrics` | component | deliver / dashboard | T, E2 | `finance-metrics-quickref`, `saas-economics-efficiency-metrics`, `saas-revenue-growth-metrics` |
| `launch-plan` | workflow | deliver / debut | T, E2 | `decision-rights-matrix`, `positioning-statement`, `press-release`, `roadmap-planning`, `stakeholder-mapping` |
| `lean-ux-canvas` | interactive | define / de-risk | T, E1 | `discovery-interview-prep`, `jobs-to-be-done`, `problem-framing-canvas`, `problem-statement`, `proto-persona` |
| `lifecycle-play-advisor` | interactive | deliver / decommission | — | `ansoff-matrix`, `organic-growth-advisor` |
| `market-landscape-scan` | workflow | determine / detect | T, E2 | `positioning-statement` |
| `message-house` | component | deliver / debut | T, E2 | `jobs-to-be-done`, `positioning-statement`, `positioning-workshop`, `proto-persona` |
| `opportunity-solution-tree` | interactive | discover / drill-down | T, E1 | — |
| `organic-growth-advisor` | interactive | determine / direct | T, E1 | — |
| `pestel-analysis` | component | determine / diagnose | T, E2 | — |
| `pestel-delta-monitor` | workflow | determine / detect | T, E2 | `derisk-measurement-advisor` |
| `pm-role-charter` | component | drive / delineate | T, E2 | `launch-metrics` |
| `pm-skill-creator` | interactive | Core / shared | — | — |
| `pm-skills-navigator` | interactive | Core / shared | — | Links to the full 90-skill lifecycle map; non-included links are external in existing bundle builds |
| `pol-probe` | component | define / de-risk | T, E2 | `discovery-process`, `problem-statement` |
| `pol-probe-advisor` | interactive | define / de-risk | — | `discovery-process`, `problem-framing-canvas`, `problem-statement` |
| `porters-five-forces` | workflow | determine / diagnose | T, E2 | — |
| `positioning-statement` | component | define / differentiate | T, E2 | — |
| `positioning-workshop` | interactive | define / differentiate | — | — |
| `prd-development` | workflow | develop / document | T, E2 | — |
| `press-release` | component | develop / document | T, E2 | — |
| `pricing-packaging-tracker` | workflow | deliver / dollars | T, E2 | `battle-card-builder`, `competitive-intel-watch`, `intelligence-collection-disciplines`, `voice-of-customer-miner` |
| `prioritization-advisor` | interactive | develop / decide | — | — |
| `problem-framing-canvas` | interactive | discover / drill-down | T, E1 | — |
| `problem-statement` | component | discover / drill-down | T, E2 | — |
| `product-lifecycle-plays` | component | deliver / decommission | T, E2 | `ansoff-matrix`, `organic-growth-advisor`, `roadmap-planning` |
| `product-sense-interview-answer` | component | drive / demystify | T, E2 | `customer-journey-map`, `opportunity-solution-tree`, `problem-statement`, `proto-persona` |
| `product-strategy-session` | workflow | determine / direct | T, E2 | — |
| `proto-persona` | component | determine / describe | T, E2 | — |
| `recommendation-canvas` | component | define / de-risk | T, E2 | — |
| `release-readiness` | component | develop / drumbeat | T, E2 | `eol-readiness-advisor`, `launch-metrics`, `launch-plan` |
| `research-synthesis` | workflow | discover / decode | T, E2 | `jobs-to-be-done`, `voice-of-customer-miner` |
| `retention-diagnostic-advisor` | interactive | deliver / deepen | — | `organic-growth-advisor`, `saas-revenue-growth-metrics`, `usage-data-investigation` |
| `roadmap-planning` | workflow | develop / decide | T, E2 | — |
| `saas-economics-efficiency-metrics` | component | determine / direct | T, E2 | — |
| `saas-revenue-growth-metrics` | component | determine / direct | T, E2 | — |
| `sales-value-narrative` | component | deliver / debut | T, E2 | `battle-card-builder`, `competitive-research-snapshot`, `positioning-statement` |
| `skill-authoring-workflow` | workflow | Core / shared | T, E1 | — |
| `sprint-planning` | workflow | develop / drumbeat | T, E2 | — |
| `stakeholder-engagement-advisor` | interactive | drive / diplomacy | — | `discovery-interview-prep` |
| `stakeholder-identification` | component | drive / diplomacy | T, E2 | `discovery-interview-prep`, `proto-persona` |
| `stakeholder-mapping` | component | drive / diplomacy | T, E2 | `discovery-interview-prep` |
| `storyboard` | component | develop / document | T, E2 | — |
| `survey-design-advisor` | interactive | discover / dig | — | `pol-probe-advisor`, `tam-sam-som-calculator` |
| `swot-analysis` | workflow | determine / diagnose | T, E2 | `battle-card-builder`, `positioning-statement` |
| `tam-sam-som-calculator` | interactive | determine / diagnose | T, E1, `scripts/market-sizing.py` | — |
| `usage-data-investigation` | workflow | discover / dig | T, E2 | `derisk-measurement-advisor`, `launch-metrics`, `saas-revenue-growth-metrics` |
| `user-story` | component | develop / draft | T, E2, `scripts/user-story-template.py` | — |
| `user-story-mapping` | component | develop / draft | T, E2 | — |
| `user-story-mapping-workshop` | interactive | develop / draft | T | — |
| `user-story-splitting` | component | develop / draft | T, E2 | — |
| `voice-of-customer-miner` | workflow | determine / describe | T, E2 | `battle-card-builder`, `discovery-interview-prep`, `opportunity-solution-tree` |
| `vp-cpo-readiness-advisor` | interactive | drive / demystify | E1 | — |
| `workshop-facilitation` | interactive | Core / shared | E1 | — |

### Command-to-plugin map

The listed components are the existing lifecycle homes of each command's
`uses` skills. Core skills are available inside every existing bundle plugin.
No individual lifecycle bundle covers every command's skill set except
`/leadership-transition`.

| Command | `uses` skill IDs → existing lifecycle component | Declared `outputs` |
|---|---|---|
| `/discover` | `discovery-process`, `problem-framing-canvas`, `discovery-interview-prep`, `opportunity-solution-tree` → Discover; `pol-probe-advisor` → Define | Discovery plan; prioritized assumptions; validation experiment backlog |
| `/leadership-transition` | `altitude-horizon-framework`, `director-readiness-advisor`, `vp-cpo-readiness-advisor`, `executive-onboarding-playbook` → Drive | Transition diagnosis; role-readiness plan; 30-60-90 leadership actions |
| `/plan-roadmap` | `roadmap-planning`, `epic-breakdown-advisor`, `prioritization-advisor`, `user-story-mapping` → Develop; `epic-hypothesis` → Define | Prioritized roadmap; epic hypotheses; release slices and sequencing rationale |
| `/prioritize` | `prioritization-advisor` → Develop; `feature-investment-advisor` → Determine; `acquisition-channel-advisor`, `finance-based-pricing-advisor` → Deliver; `recommendation-canvas` → Define | Ranked options; decision rationale; explicit tradeoffs and follow-up actions |
| `/strategy` | `product-strategy-session` → Determine; `positioning-workshop` → Define; `problem-statement`, `opportunity-solution-tree` → Discover; `roadmap-planning` → Develop | Strategy narrative; core strategic choices; sequenced roadmap direction |
| `/write-prd` | `prd-development`, `user-story`, `user-story-splitting` → Develop; `problem-statement` → Discover; `proto-persona` → Determine | Structured PRD; core personas and requirements; initial implementation-ready stories |

Each command's `outputs` are plain-language expected artifacts, not a
machine-validated schema. Its `uses` sequence is instructions in Markdown, not
an executable dependency declaration. Command frontmatter is defined in
`docs/commands.md`; repository validation checks that each referenced skill
exists. Existing commands do not declare portable plugin dependencies.
If a slash command is absent, the user-facing fallback for that row is to
explicitly invoke the listed skills in sequence, then ask the agent to
consolidate their work into the row's declared outputs.

## Evidence from current vendor documentation

Rechecked 2026-11-20:

- [Copilot CLI plugin reference](https://docs.github.com/en/copilot/reference/copilot-cli-reference/cli-plugin-reference)
  documents both legacy plugins and Agent Plugins. It recognizes Agent Plugins
  schema 1.0.0 and 1.1.0; its documented common file locations include legacy
  `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json`. A root
  Agent Plugins `plugin.json` takes precedence over `.claude-plugin/plugin.json`.
  Agent Plugins skills are in fixed `skills/` subdirectories; CLI-specific
  commands are in `com.github.copilot/commands/`. A marketplace name is its
  manifest's `name`, not its repository name.
- [Copilot CLI skill guide](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills)
  documents skill folders with optional local resources, automatic selection
  based on the task and skill description, and explicit invocation by skill
  name. It documents interactive `/skills` operations and `copilot skill`
  commands. This describes expected behavior; it does not prove that these
  skills work with an installed CLI version.
- [VS Code agent plugins](https://code.visualstudio.com/docs/agent-customization/agent-plugins)
  documents Agent Plugins and continued support for existing Copilot, Claude,
  and legacy OpenPlugin formats. `chat.plugins.enabled` enables plugins;
  `chat.plugins.marketplaces` is documented as Experimental. VS Code documents
  skills and slash commands as plugin components, but does not establish that
  this repository's current marketplace path, manifest contents, or command
  files are accepted unchanged.
- [VS Code agent plugin authoring reference](https://code.visualstudio.com/docs/agents/reference/agent-plugin-reference)
  describes the shared Agent Plugins format and namespaced
  `com.github.copilot/` components. Agent Plugins 1.0 makes skills portable;
  slash commands are client-specific, not a portable top-level component.

These pages document format capability, not a minimum Copilot CLI or VS Code
release for this repository. No supported client version is established here.

## Compatibility contract and decision

1. **Do not add a root `plugin.json`.** A root Agent Plugins manifest changes
   CLI discovery precedence over `.claude-plugin/plugin.json`; that could change
   behavior for current Claude users and the existing CLI marketplace. Keep
   `.claude-plugin/marketplace.json`, `.claude-plugin/plugin.json`, and
   `plugins/` under their existing Claude packaging/build ownership.
2. **Provisional target, contingent on client tests:** generate a separate
   all-skills Agent Plugins 1.0 package in a dedicated directory outside
   `plugins/` (for example `copilot/pm-skills-all/`) with a root `plugin.json`,
   all 95 folders under `skills/`, every local template/example/script, and
   Copilot command files only under `com.github.copilot/commands/`. The version
   1.0 schema is the conservative shared documented target; this is not yet a
   compatibility claim.
3. **Keep the repository marketplace separate:** provisionally use
   `.github/plugin/marketplace.json` with marketplace name `pm-skills-copilot`
   and a relative source into the separate generated package. These names are
   proposals, not validated identifiers. Do not modify the existing Claude
   marketplace name or entries. The current bundle generator deletes and
   rebuilds `plugins/`, so a new Copilot package must not be stored there.
4. **Preserve full skill bodies and their resources.** Do not remove
   pedagogical content or assume unknown metadata is ignored by both clients.
   The documented minimum skill frontmatter is `name` and `description`; verify
   all additional frontmatter fields in each client. If a generated copy needs
   metadata adaptation, keep it lossless and validate it against the canonical
   skill.
5. **Command contract:** current `commands/*.md` files are not currently in
   either Copilot command discovery location and are not bundled by
   `build-plugins.py`. Slash-command support exists in the documented plugin
   format, but the current command files and their `uses`/`outputs` semantics
   are not established as compatible. If clients do not load an adapted
   command, users can ask the agent to follow the workflow by name, or invoke
   the needed skill explicitly and continue through the sequence in the
   command's workflow. Don't promise `/discover`, `/strategy`, `/write-prd`,
   `/plan-roadmap`, `/prioritize`, or `/leadership-transition` until tested.
6. **Skill-use contract:** explicit skill selection and automatic selection
   must be recorded separately. Automatic selection is model-chosen, not a
   guarantee. CLI and VS Code may have different skill inventories and
   activation behavior; results in one surface or harness do not establish the
   other.

The repository names and file locations above are a safe implementation
direction based on current docs, not a final marketplace decision. The
separate generated package and marketplace should be built only after the
following client matrix passes on the actual target versions.

## Required isolated-profile validation (not run)

No client test below was run because neither CLI nor VS Code is installed in
this environment. The exact client versions, GitHub sign-in/entitlement, and
effective feature settings are therefore **unavailable**, not assumed. Do not
install into or modify a developer's existing global profile.

### Copilot CLI

Use the actual installed CLI version and an isolated `COPILOT_HOME`:

```bash
PROFILE="$(mktemp -d)"
export COPILOT_HOME="$PROFILE/copilot"
copilot --version
copilot plugin marketplace add /home/runner/work/pm-skills/pm-skills
copilot plugin marketplace list --json
copilot plugin marketplace browse pm-skills
copilot plugin install product-manager-skills@pm-skills
copilot plugin install pm-discover@pm-skills
copilot plugin list --json
copilot
```

In the interactive session, record `/skills list` and `/skills info
problem-framing-canvas`; explicitly request that skill by name and separately
ask a matching onboarding/problem-framing question without naming it. Record
whether the correct skill is loaded and whether its local resources are
available. Also try `/discover` and one bundle plugin skill; record whether
the command is discovered and whether automatic skill selection differs from
explicit selection. Do not use global install flags or an existing
`~/.copilot` directory. When testing the proposed package, use its generated
marketplace name and plugin name in the isolated profile.

### VS Code — Copilot harness

Use the actual Stable VS Code version, isolated user-data and extensions
directories, and the GitHub Copilot extension version. Sign in only inside this
throwaway profile; record the effective `chat.plugins.enabled` setting and
whether `chat.plugins.marketplaces` is required. Add the repository as a
marketplace in the Agent Plugins UI (or experimental setting), then test both
the all-skills entry and one lifecycle bundle. In Agent Customizations, verify
the plugin is listed/enabled and `problem-framing-canvas` appears under Skills.
Try explicit skill invocation and a matching prompt that does not name the
skill. Try `/discover` and record whether a slash command appears and executes.
Repeat in each target VS Code harness if more than one is in scope. Use
`--user-data-dir` and `--extensions-dir` to isolate the profile; do not change
repository settings or the developer's default profile.

### Record outcomes

| Client / harness | Client and extension versions | Feature setting | Current root + bundle manifests / marketplace | Explicit skill | Automatic skill | Existing command |
|---|---|---|---|---|---|---|
| Copilot CLI interactive | unavailable; `copilot` not installed | unavailable | blocked; not tested | blocked | blocked | blocked |
| VS Code Copilot harness | unavailable; `code` and `code-insiders` not installed | unavailable | blocked; not tested | blocked | blocked | blocked |

For each completed test, add the exact command/UI reproduction, profile
isolation method, version strings, marketplace and plugin names, skill result,
command result, and relevant warnings. A marketplace listing alone is not a
pass: confirm explicit and automatic skill use, resource resolution, and
command behavior.

## Repository checks performed

On 2026-11-20, before editing this record:

- `python3 scripts/check-bundles.py --summary` — passed; 95 skills, six bundles,
  five Core skills, every skill assigned exactly one home.
- `python3 scripts/check-command-metadata.py` — passed; all six commands
  conform and their `uses` targets exist.
- `python3 scripts/build-plugins.py --check` — passed; six generated Claude
  bundle plugins match the lifecycle config.

These repository checks validate existing source/package structure only; they
are not Copilot client tests.
