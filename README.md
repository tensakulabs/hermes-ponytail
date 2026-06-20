# hermes-ponytail

[Ponytail](https://github.com/DietrichGebert/ponytail) — lazy-senior-dev mode — packaged as a [Hermes](https://github.com/NousResearch/hermes) skills tap.

> Makes your agent think like the laziest senior dev in the room. The best code is the code you never wrote.

These are pure `SKILL.md` skills (no code, no tools, no env). Hermes loads them on demand: when a task looks over-engineered, the model pulls the skill into context and builds the simplest thing that works.

## Install

Install by explicit identifier — `<org>/<repo>/<skill>`. `--yes` skips the confirm prompt:

```bash
hermes skills install tensakulabs/hermes-ponytail/ponytail --yes
hermes skills install tensakulabs/hermes-ponytail/ponytail-review --yes
hermes skills install tensakulabs/hermes-ponytail/ponytail-audit --yes
hermes skills install tensakulabs/hermes-ponytail/ponytail-debt --yes
hermes skills install tensakulabs/hermes-ponytail/ponytail-gain --yes
hermes skills install tensakulabs/hermes-ponytail/ponytail-help --yes
```

Or grab one by raw URL, no repo prefix needed:

```bash
hermes skills install https://raw.githubusercontent.com/tensakulabs/hermes-ponytail/main/ponytail/SKILL.md
```

Skills land in `~/.hermes/skills/` and are auto-discovered on the next restart — no build step.

> Note: `hermes skills tap add tensakulabs/hermes-ponytail` registers the repo, but `hermes skills search` only queries the central hub, so tapped skills won't appear in search results. Install by the identifier above.

## Skills

| Skill | What it does |
|-------|--------------|
| `ponytail` | Lazy senior dev mode. YAGNI, stdlib first, no unrequested abstractions, shortest diff that works. |
| `ponytail-review` | Review a diff for over-engineering. One line per thing to delete. |
| `ponytail-audit` | Audit the whole repo for over-engineering. Ranked list of what to cut. |
| `ponytail-debt` | Harvest every `ponytail:` shortcut comment into one tracked debt ledger. |
| `ponytail-gain` | Scoreboard of Ponytail's measured impact (less code, less cost, more speed). |
| `ponytail-help` | Quick reference for the modes and skills. |

## Note on always-on

Upstream Ponytail runs **active every response** with a `lite|full|ultra` switch (via Claude Code / Codex hooks). Hermes skills are on-demand — there is no per-turn hook surface for a skill. If you want Ponytail governing *every* Hermes turn, append the ruleset from [`ponytail/SKILL.md`](ponytail/SKILL.md) into Hermes' base system prompt, or build it as a Hermes plugin (`pre_llm_call` hook). This repo keeps it as a normal skill, which is the ecosystem convention.

## Credit

Behavior and skill text from [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) (MIT). This repo only repackages it for Hermes.
