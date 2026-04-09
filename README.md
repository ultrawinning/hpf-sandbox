# hpf-sandbox

Execution environment for the HPFHQ autonomous build pipeline (CC Pipeline).

## Architecture

- **HPFHQ** (hpf-command-center) = control plane + data plane
  - `/spec` command on Telegram → Opus generates structured spec → Emil approves
  - `cc_specs` + `cc_queue` tables in Supabase
- **This repo** = execution plane (Session 2+)
  - Runner daemon polls `cc_queue` for queued tasks
  - Spawns `claude -p` with spec + CLAUDE.md context
  - Opens PRs on hpf-command-center after build + review passes

## Status

Session 1: Spec builder + queue tables built in HPFHQ. This repo is scaffold only.
Session 2: Builder agent, reviewer, context checker, GitHub Action or local daemon.
