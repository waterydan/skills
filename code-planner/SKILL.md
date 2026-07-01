---
name: code-planner
description: Create an implementation plan before code changes. Use when the user asks for code-planner mode, planning mode, solution design, implementation design, or wants a feature, bug fix, refactor, or technical change sharpened before any edits are made.
---

# Code Planner

## Purpose

Plan technical work before implementation.
Use this skill to interview the user, document the design, expose tradeoffs, and ask for confirmation before editing code.

## Workflow

1. Use the `$grill-with-docs` skill first when it is available.
If it is unavailable, run an equivalent focused interview and capture the important decisions in the conversation.
2. Read enough local code, docs, tests, and configuration to make the plan concrete.
Prefer project vocabulary, existing architecture, and named files over abstract guesses.
3. Use the Context7 MCP server for current documentation before planning around external libraries, frameworks, SDKs, APIs, CLIs, or cloud services.
4. Ask concise follow-up questions when requirements, constraints, or acceptance criteria are unclear.
Do not assume missing requirements when the answer materially changes the design.
5. Produce a final solution design only after the requirements are sharp enough.
Do not modify source files, tests, configs, generated assets, or implementation docs before the user confirms the plan.
Planning notes and domain docs produced by `$grill-with-docs` are allowed.
6. Ask for explicit confirmation at the end.
Stop after the plan unless the user confirms implementation.

## Final Solution Design

Present the final design as one high-level fenced code block.
Use `text` as the fence language.
Do not include actual source code, patches, or function bodies.
Do not include implementation commands unless they are validation steps.

Use this structure:

```text
Solution Design

Summary
- <what will be implemented>
- <important behavior or constraint>

Changes
- <file path>
  - <class/function/component>(<parameters>): <one-line responsibility or change>
- <file path>
  - <class/function/component>(<parameters>): <one-line responsibility or change>

Validation
- <tests, checks, or manual verification to run>

Pros
- <benefit>

Cons
- <cost, risk, or tradeoff>

Confirm?
- Reply yes to implement this design, or name changes you want first.
```

## Planning Quality

Keep the design specific enough that another agent could implement it without re-discovering the architecture.
Prefer small, cohesive changes with explicit runtime boundaries.
Call out data flow, public interfaces, migrations, tests, and UI states when relevant.
List file, class, function, component, hook, route, service, schema, and test changes by name where possible.
Use `unknown yet` only when the repo must be inspected during implementation to resolve a detail.
