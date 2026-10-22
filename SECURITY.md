# Security Policy

Applies to every repository in **The First Wall** organisation.

## Report a vulnerability

Email **security@thefirstwall.ai**, or use the incident-reporting and content-moderation portal at [thefirstwall.ai/security](https://thefirstwall.ai/security/).

Include the repository or URL, what you did, what happened, the impact — and a Base transaction hash if on-chain settlement is involved. **Do not open a public issue or pull request for a vulnerability**, and do not disclose it publicly before it is fixed.

## Rules while testing

- Test only against resources you own or are authorised to test.
- Do not move funds. Never send USDC or ETH anywhere to "prove" a finding; describe the settlement proof instead.
- Do not attack the GitHub organisation, its members, or third-party infrastructure (GitHub, Cloudflare, Base RPC providers).
- Do not read, alter or delete other people's records.

## What matters most here

1. **`pay_to` tampering.** `pay_to` must be exactly `0xbbF4D6B954e97C2C4fbC4e89B7933cDD7e4D9f23` (see `ADDRESSES.md` in the ledger repository). Any other value in `state.json`, the site, `skill.md` or an example payload is a security issue.
2. **Verifier bypass.** A claim, update or transfer that passes the CI verifier without satisfying `spec.md`.
3. **State drift.** Any way to make `state.json` disagree with the ledger data or with the on-chain anchor.
4. **Prompt injection through a claim.** Ingestion uses no language model by design; attacker-controlled text reaching a model is a finding.
5. **Supply chain.** Anything in `skill.md`, the claim skill or the x402 worker that could make a claimant sign, pay, or approve something unintended.

## What to expect

We acknowledge reports and tell you what we found. **There is no bug bounty programme** — we do not pay for reports, and a report is not a claim on funds.
