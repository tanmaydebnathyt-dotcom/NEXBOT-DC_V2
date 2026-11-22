# Security Policy — NEXBOT

We take security seriously. If you discover a vulnerability, please follow the policy below so we can triage and address it safely.

## Summary / Self-hosting clarity
NEXBOT is distributed as open-source software for self-hosting. The maintainers do not operate self-hosted instances and do not have access to user data or configurations on third-party deployments. Self-hosters are responsible for securing and operating their instances. This policy describes how to report vulnerabilities affecting the project code and provides guidance for self-hosters who discover security issues in their deployment.

## Reporting a Vulnerability
- Preferred and supported channel: open a **private GitHub Security Advisory** for this repository.
- Do **not** open a public issue with exploit details or sensitive information.
- If GitHub Security Advisories are unavailable to you, do not publish exploit details publicly; contact the repository maintainers through a private channel listed on the repository profile.

If you found a problem in your self-hosted instance that appears to be due to misconfiguration, contact the instance operator/host first. If you believe the issue is caused by a vulnerability in NEXBOT code, report it privately and indicate whether it was observed in a self-hosted deployment.

## Response timelines (what to expect)
- Acknowledgement: within 72 hours.
- Triage and severity estimate: within 7 days.
- Fix or mitigation plan:
  - Critical: aim to ship a fix or mitigation within 7–14 days.
  - High: aim to ship within 30 days.
  - Medium/Low: address in a future release; communicate within 90 days.
- Public disclosure: coordinate with the reporter and normally publish an advisory after a patch is released, or within 90 days if unresolved (unless the reporter requests otherwise).

## Safe testing rules (researcher rules of engagement)
- Only test services you own or have explicit permission to test.
- Do not exfiltrate, destroy, or modify user data.
- Do not attempt to access Discord user tokens, DMs, or other private user content.
- Provide a minimal, safe proof of concept that reproduces the issue. Redact sensitive data (tokens, personal information).
- If the vulnerability requires intrusive testing, contact the maintainers first to agree on a plan.

## What to include in your report
- Component affected (e.g., database migration, command parser, OAuth).
- Clear, minimal steps to reproduce.
- Environment: commit SHA, release tag, Docker image tag, or version.
- Whether the issue was observed on a self-hosted deployment (and the deployment configuration).
- Proof of concept (script, HTTP request, logs, screenshots); sanitize secrets before sharing.
- Impact (data exposure, privilege escalation, remote code execution, etc.).
- Suggested mitigation, if any.
- Contact information for follow-up.

## Incident reporting from self-hosted deployments
If you operate a self-hosted NEXBOT instance and suffer a security incident:
- Immediately rotate any exposed secrets (bot token, database credentials, API keys).
- Preserve relevant logs/configuration for investigation, without sharing secrets publicly.
- If you need upstream help, file a private GitHub Security Advisory and include sanitized reproduction steps and the NEXBOT version/commit.
- The maintainers can only fix vulnerabilities in upstream code; they cannot rotate tokens, restore data, or remediate other hosts' deployments.

## Scope
- In scope: this repository's code, authentication flows, webhooks provided by this project, and intended deployment artifacts (Dockerfiles, scripts).
- Out of scope: third-party services (Discord itself, hosted database providers), and instances you do not own or have permission to test.

## Maintenance and hardening advice for self-hosters
- Use TLS for all exposed endpoints and webhooks.
- Do not expose PostgreSQL to the public internet. Use an internal network, VPC, or SSH tunnel.
- Run PostgreSQL with authentication, strong passwords, and network restrictions.
- Keep secrets out of the repository (use environment variables, secret managers, or GitHub Secrets for CI).
- Restrict the bot's Discord intents and permissions to the minimum required.
- Enable automatic dependency updates (Dependabot) and repository security alerts.
- Enable secret scanning and push protection if available.
- Rotate bot tokens and API keys when compromise is suspected.
- Back up PostgreSQL regularly and test restores.
- Monitor logs and alert on suspicious activity (unexpected configuration changes, mass deletions).

## Disclosure and credits
- Researchers will be credited in release notes/advisories unless they request anonymity.
- A CVE may be assigned or coordinated with CERT/other bodies for high-severity issues.

## Privacy and telemetry
NEXBOT does not phone home or collect usage data by default. Any future telemetry must be opt-in, documented, and transparent, including what is collected and how to opt out.

Thank you for helping keep NEXBOT safe.
