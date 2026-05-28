# RunDrill Excel

Your personal **Excel coach** inside your AI agent — built to train the skill spreadsheets actually
demand: catching the **silent wrong answer**. Instead of watching the AI fill cells, you **read
formulas, predict what they return, diagnose why a result is off, and review them for bugs** — then
build to spec and score yourself against a checklist. Short targeted drills, an honest picture of your
level (novice → expert), and mistake memory that resurfaces what you got wrong. Your level and
progress live on the RunDrill MCP server (`mcp.rundrill.com`), synced across machines — not in a
local file.

**Why this course is different.** When an AI can write any formula on demand, the real risk is the
*illusion of competence* — trusting a formula that returns a number and looks right but is quietly
wrong: an unlocked `$` reference that shifts when copied, a `VLOOKUP` doing an approximate match on
unsorted data, numbers stored as text that won't sum, a PivotTable calculated field that divides
sums. RunDrill Excel trains reading, predicting, and **reviewing** formulas. Its signature drill hands
you a plausible AI-written formula with a real defect and asks you to find it — like a pull request.

The course targets **Microsoft Excel** (Sheets users can follow most of it). It climbs from the grid
and core formulas to PivotTables and dynamic arrays, then branches into specialization tracks:
**analytics & BI** (Power Query, the Data Model, DAX), **financial modeling**, **automation**
(macros/VBA, Office Scripts), and **dashboards**.

## One plugin, three hosts

The coaching skill (`skills/excel-coach/SKILL.md`) and `.mcp.json` are shared; each host reads its own
manifest and ignores the rest.

| Host | Reads |
|---|---|
| Claude Code / Claude Desktop | `.claude-plugin/plugin.json` + `.mcp.json` |
| OpenAI Codex | `.codex-plugin/plugin.json` + `.mcp.json` |
| Google Antigravity | `plugin.json` + `mcp_config.json` (+ `rules/`) |

The MCP endpoint is `https://mcp.rundrill.com/skills/excel` — the skills-course host, passing
`subject: "excel"`. The server routes on the `/skills` segment and ignores the course name; the name
makes Excel register as its own MCP server in your agent. On first use the host opens a browser tab
for the OAuth handshake, then closes it — no API key to paste.

## Install

- **Claude Code / Desktop** — via the RunDrill marketplace:
  ```
  /plugin marketplace add rundrill/rundrill
  /plugin install rundrill-excel@rundrill
  ```
  Then run `/excel-coach`.
- **OpenAI Codex** — `codex plugin marketplace add rundrill/rundrill`, then install `rundrill-excel`.
- **Google Antigravity** — drop this folder into `~/.gemini/config/plugins/rundrill-excel/` (global)
  or `<workspace>/.agents/plugins/rundrill-excel/` (workspace-scoped).

## License & attribution

© RunDrill. Licensed under **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0
International (CC BY-NC-ND 4.0)** — full text in [LICENSE](LICENSE). You may view, run, and share this
plugin unchanged, non-commercially, with attribution; you may not use it commercially or publish
modified/derivative versions. For other licensing, contact **hello@rundrill.com**.
