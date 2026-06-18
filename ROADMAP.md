# Roadmap

This tracks where txio is headed, built directly from the open issue backlog on
[Txio-labs/txio](https://github.com/Txio-labs/txio/issues). Priorities are labeled
`priority:critical` / `priority:high` / `priority:medium` / `priority:low` on each issue —
that's the source of truth; this file is a summary, not a separate plan.

## Shipped

- Unified CLI across Sui, Ethereum, Solana, Aptos, and Soroban (`cli/`), with a
  `ChainAdapter` trait so a new chain is one file + a factory registration.
- Axum/MongoDB backend (`backend/api/`) serving auth, collections, workspaces,
  and SuiNS name resolution to both the CLI and the dashboard.
- Next.js dashboard (`frontend/`) — Postman-style request builder, visual PTB
  builder, collection runner, AI console.
- One-command local stack via `docker-compose up`.

## Now — security hardening (blocking further feature work)

These are `priority:critical` and touch auth/execution paths directly:

- [#1](https://github.com/Txio-labs/txio/issues/1) Account takeover via unauthenticated user-management endpoints
- [#2](https://github.com/Txio-labs/txio/issues/2) Unauthenticated remote command execution via `/terminal/execute`

## Next — high-priority fixes

- [#3](https://github.com/Txio-labs/txio/issues/3) Registration doesn't reject duplicate emails
- [#4](https://github.com/Txio-labs/txio/issues/4) OTP flow lacks rate limiting / brute-force protection
- [#5](https://github.com/Txio-labs/txio/issues/5) AI chat proxy is unauthenticated and unthrottled (cost abuse)
- [#10](https://github.com/Txio-labs/txio/issues/10) SSRF via user-controlled `rpc_url` on saved request execution
- [#11](https://github.com/Txio-labs/txio/issues/11) JWT stored in localStorage, leaked in OAuth redirect URL
- [#18](https://github.com/Txio-labs/txio/issues/18) CI never compiles or tests the Rust backend/CLI
- [#29](https://github.com/Txio-labs/txio/issues/29) CLI is a fat client requiring DB creds; `db` subcommands are unauthenticated admin

## Later — medium-priority hardening and correctness

CORS, container hardening, config/DB consistency, and a handful of stubbed
features (ENS resolution, CLI `profile`/`wallet`/`console` commands) that are
advertised but not implemented yet. Full list: issues
[#6](https://github.com/Txio-labs/txio/issues/6),
[#7](https://github.com/Txio-labs/txio/issues/7),
[#9](https://github.com/Txio-labs/txio/issues/9),
[#12](https://github.com/Txio-labs/txio/issues/12)–[#17](https://github.com/Txio-labs/txio/issues/17),
[#19](https://github.com/Txio-labs/txio/issues/19)–[#22](https://github.com/Txio-labs/txio/issues/22),
[#25](https://github.com/Txio-labs/txio/issues/25),
[#27](https://github.com/Txio-labs/txio/issues/27).

## Good first issues

Smaller, self-contained, and a good way to make a first contribution:
[#8](https://github.com/Txio-labs/txio/issues/8) (wrong repo name in README/Cargo.toml),
[#23](https://github.com/Txio-labs/txio/issues/23) (inconsistent network enums),
[#24](https://github.com/Txio-labs/txio/issues/24) (lossy `as f64` balance formatting),
[#26](https://github.com/Txio-labs/txio/issues/26) (backend container runs as root),
[#28](https://github.com/Txio-labs/txio/issues/28) (deprecated/duplicate Sui SDKs in frontend),
[#30](https://github.com/Txio-labs/txio/issues/30) (OTP records never expire — add TTL index).

## Exploratory

- Finish the Electron desktop client (`desktop/`) to parity with the web dashboard.
- Expand name resolution beyond `.sui` (ENS for `.eth`, equivalents for Aptos/Soroban).
- Reconcile the AI console between the documented Groq backend and the
  Gemini-based flow described in the frontend docs.
