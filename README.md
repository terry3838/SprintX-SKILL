# SprintX OpenClaw Handoff Skill

Public standalone repo for the first SprintX ClawHub skill.

This repo publishes an instruction-first OpenClaw skill that guides operators through the smallest SprintX handoff proof packet:

`sx auth -> sx project use -> sx event -> sx artifact add -> sx status -> sx brief`

The repo is intentionally narrow. It does not add a custom MCP server, hidden SprintX automation, or broad natural-language control.

한국어 요약:
- 이 저장소는 SprintX의 첫 공개 OpenClaw skill 저장소입니다.
- 기본 경로는 `sx auth -> sx project use -> sx event -> sx artifact add -> sx status -> sx brief` 입니다.
- 자세한 한글 문서는 `references/source-of-truth.md` 링크를 보세요.

## What Lives Here

- `SKILL.md` — the only operator-truth document for the skill
- `references/source-of-truth.md` — upstream docs and publish references
- `scripts/` — local validation scripts for frontmatter and instruction contract
- `.github/workflows/ci.yml` — repo validation only, not auto-publish

## Release Model

This repo uses validation CI plus manual ClawHub publish.

Validation:

```bash
npm run check
```

Publish:

```bash
clawhub publish . \
  --slug sprintx-openclaw-handoff \
  --name "SprintX OpenClaw Handoff" \
  --version 0.1.0 \
  --tags latest \
  --changelog "Initial release"
```

We keep publish manual on purpose. The current ClawHub docs clearly support CLI-driven skill publish, while plugin/package auto-publish flows are more mature than skill auto-publish flows today.

Note:
- In the locally verified `clawhub` CLI (`v0.9.0`), the working command is top-level `clawhub publish <path>`.
- Some upstream docs still describe `clawhub skill publish`. Re-check the installed CLI help before cutting a release.

## Local Layout

```text
SprintX-SKILL/
├── .github/workflows/ci.yml
├── CHANGELOG.md
├── LICENSE
├── README.md
├── SKILL.md
├── package.json
├── references/
│   └── source-of-truth.md
└── scripts/
    ├── check-contract.mjs
    └── check-skill.mjs
```
