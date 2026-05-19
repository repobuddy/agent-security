# AGENTS.md

This file provides guidance to AI coding assistants when working with code in this repository.

## What This Repo Is

Skills for AI agents to detect and remediate security vulnerabilities in JavaScript/TypeScript repositories — fixing failed PRs, resolving audit failures, and patching vulnerable dependencies.

## No Build or Test System

Pure markdown. No build, lint, or test commands. The `npx skills` CLI is used by consumers to install skills, not by contributors.

## Adding a New Skill

Create `skills/<skill-name>/SKILL.md` with this structure:

```markdown
---
name: skill-name
description: "One sentence trigger description — WHAT it does, WHEN to invoke it, key situations it handles."
---

# Skill Title

...content...
```

For sub-skills (called by other skills, not triggered by user situation), prefix the description with `"Internal skill:"` to prevent accidental activation.

## Skill Design Principles

- **Decisions over documentation** — encode what to decide and how, not reference material the model already knows
- **Narrow and composable** — one workflow per skill; user-facing skills match situations, sub-skills are called explicitly by other skills
- **No baked-in opinions** — detect the user's setup at runtime rather than assuming a specific stack
