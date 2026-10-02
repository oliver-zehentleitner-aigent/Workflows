# Compute policy

## Budget-aware tiering over pure routing (Milestone 7)

**Id:** 92ea0015-c1df-4080-856a-6f2637bdb80a  
**Status:** active  
**Evidence:** confirmed  
**Source:** M7 commit `fce312c`; `packages/policy/`; `POLICY_ENABLED` default false  
**See:** observability.md#local-jsonl-events-not-saas-milestone-8 — 205def52-1c76-4e26-b2fa-d2898ecaed54 — as of 2026-10-02
**See:** routing.md#rule-based-local-vs-frontier-selection-milestone-0 — fb4c984d-072a-413e-941c-c656d77126c2 — as of 2026-10-02

Rule routing alone cannot **cap cost**. Compute policy sits before model selection: session/daily budgets, optional mid tier, force flags, and a recorded reason. When `POLICY_ENABLED` is false, behavior matches the prior router-only path.

**Reason:** Frontier and mid-tier spend should be intentional. Operators need budgets and an explicit opt-in before habitual paid traffic.

**Rejected alternatives:**

- **Only hardcode more router rules** — cannot enforce remaining budget or daily USD caps.
- **Policy always on with aggressive defaults** — would change M0 behavior unexpectedly; default off preserves the known path.
- **Dynamic vendor price APIs / multi-cloud arbitrage** — out of scope for the shell.

See also [routing.md](routing.md) (task/complexity rules) and [observability.md](observability.md) (policy reason on events).
