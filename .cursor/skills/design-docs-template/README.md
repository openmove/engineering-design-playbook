# Design docs template — agent skills (OpenMove)

Commands for the **RFC → ADR → arc42 + Starlight** workflow. This copy lives in **OpenMove’s** [engineering-design-playbook](https://github.com/openmove/engineering-design-playbook).

## The idea

You only install **this skill**. Then you ask the agent to **bootstrap**: it creates the docs project from the OpenMove GitHub template (folders, Starlight, and these skills already inside). You do not clone templates by hand to get started.

```text
install skill (once)  →  /design-docs-template → bootstrap  →  repo ready
```

After that, in the new repo: `new-rfc`, `preview`, `rfc-hygiene`, `close-loop`, …

## Install the skill (once per agent)

Pick your tool. One command. Restart the agent (or open the project) afterward.

Source repo for every install line: `openmove/engineering-design-playbook`.

### Cursor

**Personal** (all projects): put the folder in your Cursor user/Agent Store `skills/design-docs-template/`, or ask Agent: “install the design-docs-template skill from `openmove/engineering-design-playbook`”.

**This repo only:**

```bash
npx --yes degit openmove/engineering-design-playbook/.cursor/skills/design-docs-template .cursor/skills/design-docs-template
```

Then: Agent chat → `/design-docs-template` → **bootstrap**.

### Claude Code

**Personal:**

```bash
npx --yes degit openmove/engineering-design-playbook/.claude/skills/design-docs-template ~/.claude/skills/design-docs-template
```

**This repo only:**

```bash
npx --yes degit openmove/engineering-design-playbook/.claude/skills/design-docs-template .claude/skills/design-docs-template
```

Then: `/design-docs-template` → **bootstrap**.

Docs: [Claude skills](https://code.claude.com/docs/en/skills).

### ChatGPT / Codex

**Personal:**

```bash
npx --yes degit openmove/engineering-design-playbook/.agents/skills/design-docs-template ~/.agents/skills/design-docs-template
```

**This repo only:**

```bash
npx --yes degit openmove/engineering-design-playbook/.agents/skills/design-docs-template .agents/skills/design-docs-template
```

Then invoke `design-docs-template` from the skills list → **bootstrap**.

Docs: [Codex / ChatGPT skills](https://learn.chatgpt.com/docs/build-skills).

### Pi

Same path as Codex (recommended):

```bash
npx --yes degit openmove/engineering-design-playbook/.agents/skills/design-docs-template ~/.agents/skills/design-docs-template
```

Or project-local: same command into `.agents/skills/design-docs-template`.

Then: `/skill:design-docs-template` → **bootstrap**. Use `/reload` after changing the skill.

Docs: [Pi skills](https://pi.dev/docs/latest/skills).

## Project vs personal

| Scope | Where | When |
| --- | --- | --- |
| **Personal** | `~/.cursor` / Agent Store, `~/.claude/skills`, `~/.agents/skills` | You want **bootstrap** available before any docs repo exists |
| **Project** | `.cursor/skills`, `.claude/skills`, `.agents/skills` in the repo | Team shares the workflow; also what **bootstrap** leaves in a new repo |

**bootstrap** creates the project via `gh repo create --template openmove/engineering-design-playbook`, so the new repo already contains all three skill paths.

## Commands

| Command | What it does |
| --- | --- |
| **bootstrap** | Creates a new docs repo from the OpenMove GitHub template and rebrands site config. |
| **new-rfc** | Next numbered RFC + index. |
| **new-adr** | Next numbered ADR (MADR) + index. |
| **rfc-hygiene** | Cleans a noisy draft RFC (names, diagrams, examples, stale prose). |
| **close-loop** | Approved RFC → ADR(s) + arc42/C4 checklist. |
| **preview** | Sync + local Starlight; prints URL with `base`. |

## Method (one screen)

| You are… | Write | Can it change? |
| --- | --- | --- |
| Still deciding | **RFC** | Yes until accepted, then history |
| Recording a choice | **ADR** | Never edit accepted; supersede |
| Describing the system today | **arc42 + C4** | Yes — update when the RFC closes |

## Template

| Flavour | GitHub |
| --- | --- |
| **OpenMove (this repo)** | [openmove/engineering-design-playbook](https://github.com/openmove/engineering-design-playbook) |
| Generic upstream | [alessandroros/design-docs-template](https://github.com/alessandroros/design-docs-template) |
