# NorCal Inspection — Internal Tooling Skill

## Architecture
- HTML/JS tools hosted on GitHub Pages (https://norcal-inspection.github.io/norcal-tools)
- Cloudflare Workers as a CORS proxy for any API calls (https://smartsheet-proxy.rebecca-91f.workers.dev)
- Smartsheet as the data destination, accessed via the proxy
- PDF parsing done locally in the browser via PDF.js (no server cost)
- Tools are used by non-technical team members — no installation, no terminal, no code required

## Deployment Workflow
- HTML/JS changes: save to local repo folder → commit and push in GitHub Desktop → live in ~30 seconds
- Cloudflare Worker changes: deploy via `wrangler deploy` from Terminal

## Working Agreements
- Fully agree on requirements and approach before any code is written
- During QA: diagnose and confirm root cause before proposing fixes, confirm the fix before implementing, verify with a test before shipping
- No shooting in the dark
- These are defaults — any parameter can be overridden in a session if explicitly stated

## Requirements Gathering (start of every new tool)
- Establish audience, usage frequency, technical environment, and failure tolerance
- Identify all edge cases by examining real data before building, not during QA

## Known Mac Gotchas (for any .command scripts)
- Gatekeeper: user runs `xattr -d com.apple.quarantine /path/to/file.command` once after download
- Drag-and-drop path escaping: use `read -rp "..." RAW_VAR` then `EVAL_VAR=$(eval echo "$RAW_VAR")`
