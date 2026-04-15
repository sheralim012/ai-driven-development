---
title: AI-Driven Development
sub_title: Training Plan for Engineering Team
author: Sher Ali
---

<!-- jump_to_middle -->

Why This Training?
===

<!-- end_slide -->

The Shift
===

AI is no longer just an assistant that autocompletes your code.

<!-- pause -->

It is a **sparring partner**, a knowledge base you can talk with, and a collaborator that can brainstorm, plan, generate, and test alongside you.

<!-- pause -->

**Core Principle:**
Treat AI as your sparring partner, not your autopilot.

<!-- pause -->

The AI helps you think — but **you own the decisions**.

<!-- end_slide -->

What You Will Learn
===

<!-- incremental_lists: true -->

* How to choose the right AI-driven development framework for a given task
* How to brainstorm, plan, and generate implementation artifacts using AI
* How to review every AI output with discipline and precision
* How to write effective prompts that produce high-quality results
* How to recognize and recover from common AI failure modes
* How to collaborate with DMs and SQA in an AI-driven workflow
* How to manage context across sessions for consistency

<!-- end_slide -->

<!-- jump_to_middle -->

Section 1: Framework Selection
===

<!-- end_slide -->

The Four Approaches
===

**Standard Claude (On-the-fly)**
Direct prompting, planning mode, conversational. No rigid structure.
Best for exploration, quick tasks, and working within existing codebases.

<!-- pause -->

**B-MAD**
Full plan upfront, full implementation detail before any code.
Requires high requirements clarity. Works extremely well for well-defined, traditional systems.

<!-- end_slide -->

The Four Approaches (continued)
===

**Get Shit Done (GSD)**
Documentation-heavy, designed for rapid MVP generation.
Double-edged sword — comprehensive but time-consuming to review.

<!-- pause -->

**Superpowers**
Balanced documentation. Follows TDD: AI writes failing tests → writes code → iterates until all tests pass.
Structured enough to keep AI aligned, lightweight enough to stay efficient.

<!-- end_slide -->

How to Choose: Requirements Clarity
===

| Clarity Level | Approach |
|---|---|
| Crisp, well-understood (CRUD, known API) | **B-MAD** |
| Partially defined, still forming | **Superpowers** |
| Exploratory or throwaway | **Standard Claude / GSD** |

<!-- end_slide -->

How to Choose: Scope & Complexity
===

| Scope | Approach |
|---|---|
| Large, multi-module system | **B-MAD** |
| Medium feature, 3-5 files | **Superpowers** |
| Small isolated task, utility, script | **Standard Claude** |

<!-- end_slide -->

How to Choose: Codebase Maturity
===

| Codebase State | Approach |
|---|---|
| Greenfield (from scratch) | **B-MAD or Superpowers** |
| Existing codebase, adding features | **Superpowers** with context |
| Legacy or messy codebase | **Standard Claude** to understand, **Superpowers** for new modules |

<!-- end_slide -->

How to Choose: Time vs Quality
===

| Situation | Approach |
|---|---|
| Need it today, doesn't need to be perfect | **GSD** |
| Production quality, have time | **Superpowers or B-MAD** |
| Decent quality, reasonable timeline | **Superpowers** (lighter review) |

<!-- end_slide -->

Quick Reference
===

| Scenario | Approach |
|---|---|
| Well-defined system, clear spec | B-MAD |
| Medium feature, production quality | Superpowers |
| Quick MVP or proof of concept | GSD |
| Exploratory prototype or spike | Standard Claude |
| Bug fix or small isolated task | Standard Claude |
| New module in existing codebase | Superpowers (with context) |
| Full greenfield system | B-MAD or Superpowers |
| Refactoring existing code | Standard Claude |

<!-- end_slide -->

Important Note
===

These are **tools in a toolkit**, not religions to follow.

<!-- pause -->

You might start with Standard Claude for brainstorming, switch to Superpowers for implementation, and drop back to Standard Claude for quick fixes during testing.

<!-- pause -->

**Match the tool to the moment.**

<!-- end_slide -->

<!-- jump_to_middle -->

Section 2: The Workflow
===

<!-- end_slide -->

End-to-End Flow
===

```
Brainstorming
    → PRD / Project Brief
        → Implementation Plan
            → Phase / Module Division
                → Code & Test Generation (TDD loop)
                    → Code Review
                        → Manual Verification
                            → Git Commit
                                → Next Module
```

<!-- end_slide -->

Phase 1: Brainstorming
===

Use AI as a **brainstorming partner**.

<!-- pause -->

Dictate your ideas, converse with them, let the AI help you formalize and find gaps.

<!-- pause -->

This is especially valuable if you're not strong on product sense — the AI helps you structure your thinking.

<!-- pause -->

**Output:** A PRD or project brief — a high-level overview of the product.

<!-- end_slide -->

Phase 2: Implementation Plan
===

Generate an implementation plan from the PRD.

<!-- pause -->

This is the **most critical artifact** in the entire workflow.

<!-- pause -->

> The coding will be as good as your implementation plan.

<!-- pause -->

It doesn't matter if reviewing takes **three or four days** — it will pay dividends during implementation.

**Spend the time here.**

<!-- end_slide -->

Phase 3: Task Division
===

Divide the implementation plan into:
* Phases
* Milestones
* Modules
* Epics

<!-- pause -->

Define dependencies. Identify parallel vs. sequential tasks.

AI can assist with this breakdown.

<!-- end_slide -->

Phase 4: Module Execution
===

Start with a **single module**. Follow the loop:

<!-- incremental_lists: true -->

1. AI generates test cases and writes code through the TDD loop (failing tests → code → iterate until passing)
2. You review the generated code and test cases
3. Manually verify the results
4. AI generates a commit message → you review and commit to Git

<!-- pause -->

**Master this level before proceeding to the next module.**

<!-- end_slide -->

Phase 5: Commit Discipline
===

Every completed module must be committed or made into a PR. **This is not optional.**

<!-- pause -->

Git history is your **undo button**. If a module gets messed up, you revert and start from scratch.

<!-- pause -->

**Commit messages are generated by AI as well.** Review them the same way you review code — make sure they accurately describe the change.

<!-- pause -->

**Commit module by module.** These are your checkpoints.

<!-- end_slide -->

<!-- jump_to_middle -->

Section 3: Review Process
===

<!-- end_slide -->

Why Review Discipline Matters
===

"Review everything" is correct but insufficient.

<!-- pause -->

Without defining **what to look for**:
* Senior engineers **over-review** and waste time
* Junior engineers **under-review** because they don't know what matters
* Mid-level engineers review **inconsistently**

<!-- pause -->

**Principle: Front-load your review effort.**

Spend the most time on PRD and implementation plan, less on tests, least on code.

<!-- end_slide -->

Reviewing the PRD
===

The AI produces something that **reads well**. The risk is accepting it without verifying intent.

<!-- pause -->

**Checklist:**

<!-- incremental_lists: true -->

* **Scope accuracy** — Did AI add features you didn't ask for?
* **Assumptions surfaced** — Are they explicit or buried?
* **User/actor clarity** — Admins, managers, employees, external clients?
* **What's excluded** — Is out-of-scope stated?
* **Domain language** — Your terminology or the AI's?

<!-- pause -->

**Time: 30-60 minutes**

<!-- end_slide -->

Reviewing the Implementation Plan
===

Every gap here becomes a bug or wasted effort later.

**Checklist:**

<!-- incremental_lists: true -->

* **Architecture decisions** — Appropriate for your project?
* **Data model** — Missing fields? Incorrect relationships? Wrong cardinality?
* **Dependency order** — Can you actually build A before B?
* **API contracts** — Interfaces match across modules?
* **Edge cases** — What happens with null? When API fails? Concurrent users?
* **Step feasibility** — Is AI hiding substeps in compressed instructions?

<!-- pause -->

**Time: 2-4 hours** (spread across days for large projects)

<!-- end_slide -->

Reviewing Test Cases
===

AI writes tests based on **its understanding**, not yours. If it misunderstood, tests pass for wrong behavior.

**Checklist:**

<!-- incremental_lists: true -->

* **Match your intent**, not just the spec
* **Missing negative tests** — invalid inputs, unauthorized access, boundaries
* **Missing integration scenarios** — module A calling module B
* **Hardcoded assumptions** — asserting exact values that should be configurable
* **Quality over quantity** — redundant tests vs. meaningful gaps

<!-- pause -->

**Time: 20-40 minutes per module**

<!-- end_slide -->

Reviewing AI-Generated Code
===

If upstream reviews were solid, code should be largely correct. Focus shifts to **clean, safe, maintainable**.

**Checklist:**

<!-- incremental_lists: true -->

* **Matches the plan?** Literally — if plan said "use repository pattern," verify it
* **Naming conventions** — follows your team's style?
* **Security** — hardcoded secrets, missing auth checks, exposed errors
* **Input validation** — AI frequently skips field lengths, format checks, required fields
* **Error handling** — caught, logged, handled gracefully?
* **Performance** — N+1 queries, missing pagination, loading everything into memory?
* **Dead code** — unused helpers, over-engineered abstractions?

<!-- pause -->

**Time: 30-60 minutes per module**

<!-- end_slide -->

Input Validation: AI's Biggest Blind Spot
===

AI **frequently skips** field-level validation:

<!-- pause -->

* Maximum/minimum lengths
* Allowed characters
* Required fields
* Format validation (email, phone, URL)

<!-- pause -->

**Examples:**

* Django `CharField` without `max_length`
* FastAPI schema missing `Field(max_length=255)`
* Next.js forms skipping client-side length checks

<!-- pause -->

**Always verify every model and serializer for missing constraints.**

<!-- end_slide -->

<!-- jump_to_middle -->

Section 4: Prompt Engineering
===

<!-- end_slide -->

Why Prompting Matters
===

Every framework assumes you can effectively communicate intent to the AI.

<!-- pause -->

The gap between how a **senior** prompts and how a **junior** prompts produces dramatically different outputs from the **same tool**.

<!-- pause -->

Prompting requires **precision like code** but **flexibility like natural language**.

<!-- end_slide -->

Skill 1: Context Setting
===

The biggest mistake: jumping to the task without establishing context.

**Good context example:**

```
"We're building a multi-tenant SaaS for HR management.
 Backend: Python with Django REST Framework, PostgreSQL.
 Frontend: Next.js with TypeScript.
 Background tasks: Celery + Redis.

 Auth module is built using djangorestframework-simplejwt.
 User model extends AbstractUser with custom fields.
 We're now building the employee management module.

 Constraints: existing schema, no new pip packages without
 approval, all endpoints use IsAuthenticated,
 serializer-view-service pattern."
```

<!-- pause -->

**Rule:** Spend 2-3 minutes writing context before your first prompt. It's the AI's onboarding.

<!-- end_slide -->

Skill 2: Scoping
===

Don't combine multiple asks. AI does everything at 70% instead of one thing at 95%.

<!-- pause -->

**Too broad:**
"Build the notification system."

<!-- pause -->

**Too narrow:**
"Write line 42 of the notification service."

<!-- pause -->

**Right scope:**
"Create the notification service in `apps/notifications/services.py` for in-app notifications. Accept user ID, type, title, body. Store in Notification model, mark unread. Create model, serializer, viewset. Don't implement email or Slack yet."

<!-- pause -->

**Rule:** If your prompt is longer than two paragraphs, break it up.

<!-- end_slide -->

Skill 3: Negative Constraints
===

Tell the AI what **NOT** to do. This prevents the most common failure mode: technically correct but contextually wrong.

<!-- incremental_lists: true -->

* "Do not modify any existing files. Only create new files."
* "Do not install new pip packages. Use only requirements.txt."
* "Do not change existing Django models or run makemigrations."
* "Do not implement authentication — handled by DRF permission classes."
* "Do not use class-based views. Function-based with @api_view only."
* "Do not use Next.js Pages Router. App Router exclusively."

<!-- pause -->

**Rule:** 30 seconds of constraint writing prevents 30 minutes of debugging.

<!-- end_slide -->

Skill 4: Course Correction
===

The AI **will** drift. Don't start over (wasteful) or keep layering on broken output (worse).

<!-- pause -->

**Identify the drift, not the symptom:**
"You implemented a REST endpoint, but I need a background Celery task on a cron schedule."

<!-- pause -->

**Restate intent:**
"The function returns a flat list, but I need a nested tree — each department contains its employees."

<!-- pause -->

**Use examples** when words aren't enough — show sample input and expected output.

<!-- pause -->

**Rule:** Two corrections on the same issue = signal. Rewrite your prompt or break the task down.

<!-- end_slide -->

Skill 5: Context Across Sessions
===

AI doesn't remember your last session. Every conversation starts from zero.

<!-- incremental_lists: true -->

* **Project context file** — markdown summarizing current state. Load every session.
* **Skills/rules files** — persistent behavioral instructions for the AI.
* **Carry forward outputs, not conversations** — the plan, the code, the tests.
* **Session handoff** — ask AI to summarize what was done and what's next.

<!-- pause -->

**Rule:** If you explain the same thing in 2+ sessions, it belongs in your context file.

<!-- end_slide -->

<!-- jump_to_middle -->

Section 5: Failure Modes & Recovery
===

<!-- end_slide -->

General Recovery Principle
===

<!-- jump_to_middle -->

> The fastest recovery is almost always **"revert and regenerate with better input"** rather than "debug and patch the wrong output."

<!-- end_slide -->

Failure 1: The Confident Wrong Answer
===

**What:** Code that's clean, passes tests, and is **fundamentally wrong**. Business logic is plausible but incorrect.

<!-- pause -->

**Why dangerous:** Tests pass because they're based on the same wrong assumption.

<!-- pause -->

**Catch it:** Trace test scenarios against actual business rules. "If real users did this, would it be correct?"

<!-- pause -->

**Recover:** Don't patch the code. Fix the **implementation plan**, then regenerate.

<!-- end_slide -->

Failure 2: Hallucinated Dependencies
===

**What:** AI imports packages that don't exist, uses deprecated methods, or wrong function signatures.

<!-- pause -->

**Catch it:** Scan imports before running. Verify unfamiliar packages. Check method signatures against your version.

<!-- pause -->

**Recover:** Tell AI the **exact version** and provide correct API surface. Don't just say "that doesn't exist" — it will guess again.

<!-- end_slide -->

Failure 3: Context Window Overflow
===

**What:** AI "forgets" earlier instructions. Reverts to defaults. Quality degrades gradually.

<!-- pause -->

**Catch it:** If you're repeating instructions, or AI does something you prohibited — context is the issue.

<!-- pause -->

**Recover:** Start a **fresh session**. Carry forward artifacts only, not conversation history.

<!-- pause -->

**Guideline:** Plan for 2-3 sessions per complex module. Define scope per session.

<!-- end_slide -->

Failure 4: The Integration Mismatch
===

**What:** Module A works alone. Module B works alone. Together, nothing works. API contracts don't match.

<!-- pause -->

**Catch it:** Define interfaces at the **implementation plan stage**, not during coding.

<!-- pause -->

**Recover:** Identify which module's interface is "correct" per the architecture. Fix the other. Regenerate with explicit interface constraints.

<!-- end_slide -->

Failure 5: The Refactor Trap
===

**What:** You ask for a feature. AI renames variables, restructures files, changes patterns. Diff is 400 lines instead of 20.

<!-- pause -->

**Catch it:** Check scope before accepting. One endpoint requested, six files changed = problem.

<!-- pause -->

**Recover:** Revert entirely. Reprompt: "Add [feature]. Do not modify existing code. Do not rename. Do not refactor. Minimum necessary changes only."

<!-- end_slide -->

Failure 6: Test Suite False Confidence
===

**What:** Tests pass, coverage looks good, but tests check **implementation details** instead of **behavior**.

<!-- pause -->

**The test:** "If I rewrote the implementation but kept the same behavior, would tests still pass?"

If no → they're testing implementation, not behavior.

<!-- pause -->

**Recover:** Keep behavioral tests. Supplement with your own. Sometimes writing tests yourself is faster.

<!-- end_slide -->

<!-- jump_to_middle -->

Section 6: SQA in AI-Driven Development
===

<!-- end_slide -->

The Problem
===

The TDD loop is **self-referential** — AI is both author and judge.

<!-- pause -->

SQA engineers break this loop by providing an **independent quality perspective** rooted in the PRD and end-user experience.

<!-- pause -->

SQA doesn't need to know the implementation details. They verify the system does what the **PRD says it should**.

<!-- end_slide -->

SQA Phase 1: Test Scenarios from PRD
===

SQA's primary input is the **PRD, not the code**.

<!-- incremental_lists: true -->

* **UAT scenarios** — walk through every user flow. "Employee submits leave → Manager gets notification → Manager approves → Balance updates"
* **Edge cases devs will miss** — empty optional fields, concurrent edits, date boundaries, special characters
* **Boundary conditions** — max field lengths, zero quantities, empty lists, very long strings

<!-- pause -->

AI frequently skips input validation — **SQA should explicitly test these.**

<!-- end_slide -->

SQA Phase 2: UAT & Verification
===

After the developer completes and commits a module:

<!-- incremental_lists: true -->

* Does behavior match what the **PRD describes**?
* Do UAT scenarios pass when tested manually?
* Are there behaviors that look correct in code but **feel wrong** as an end user?
* Does this module work with **previously built modules**?

<!-- end_slide -->

SQA Phase 3: Bug & Enhancement Reporting
===

SQA prepares structured reports that devs can **hand directly to AI** as prompts.

Each item must include:

<!-- incremental_lists: true -->

* **Title:** "Employee name field accepts input beyond 255 characters"
* **Expected:** Validation error shown to user
* **Actual:** 500 server error returned
* **Steps to reproduce:** Exact sequence
* **Severity:** Critical / Major / Minor / Enhancement

<!-- pause -->

**The more specific the report, the better the AI performs when fixing it.**

Vague: "form doesn't work right" → vague AI output.

Specific: "CharField missing max_length constraint" → precise fix.

<!-- end_slide -->

<!-- jump_to_middle -->

Section 7: Team Collaboration
===

<!-- end_slide -->

Single-Developer Module Ownership
===

Each module is owned by a **single developer** from start to finish.

<!-- pause -->

**No handoffs between developers on the same module.**

<!-- pause -->

Why? AI-driven development relies on accumulated context. Handing a module to another developer means **losing that context**, leading to inconsistent code.

<!-- pause -->

If the developer is unavailable, the module **waits or restarts from scratch** — not picked up mid-stream.

<!-- end_slide -->

The Three Roles
===

**Developer**
* Owns the entire build loop for assigned modules
* Collaborates with DM on plan review, SQA on quality
* Reviews AI-generated commit messages and commits
* Incorporates SQA bug reports by feeding them to AI

<!-- pause -->

**Delivery Manager**
* Reviews and approves PRD and implementation plan
* Divides plan into module assignments
* Tracks progress through ClickUp

<!-- pause -->

**SQA Engineer**
* Creates test scenarios from PRD
* Owns UAT and edge case discovery
* Produces structured bug/enhancement lists for the dev

<!-- end_slide -->

The Collaboration Flow
===

```
DM reviews PRD
    → Developer generates implementation plan
        → DM reviews plan
            → Developer builds module (AI TDD loop)
                → SQA tests from PRD
                    → SQA submits bug/enhancement list
                        → Developer feeds list to AI for fixes
                            → SQA re-verifies
                                → Developer commits
                                    → ClickUp task updated
```

<!-- end_slide -->

ClickUp Integration
===

Each module maps to a ClickUp task containing:

<!-- incremental_lists: true -->

* Relevant section of the implementation plan
* Framework being used (B-MAD, Superpowers, etc.)
* Dependencies on other tasks
* Acceptance criteria from PRD and SQA scenarios
* Checklist: plan reviewed → code generated → SQA tested → bugs addressed → committed

<!-- pause -->

Update task status as you progress. Keeps DM informed without status meetings.

<!-- end_slide -->

<!-- jump_to_middle -->

Section 8: Context Management
===

<!-- end_slide -->

What Must Persist Between Sessions
===

**1. Project Context Document**

A living markdown file — current state, not history:
* Tech stack and versions
* Folder structure, naming conventions
* Architecture patterns in use
* What's built, what's in progress, what's next

<!-- pause -->

Load at session start. Update after every module. Keep it concise.

<!-- end_slide -->

What Must Persist (continued)
===

**2. Skills/Rules Files**

Persistent behavioral instructions:

```
"Always use async views with FastAPI, sync with DRF"
"All API responses: {'success': bool, 'data': ..., 'error': ...}"
"Database queries through services.py, never in views"
"All serializers must include field-level validation"
"Next.js: Server Components by default, 'use client' only when needed"
```

<!-- pause -->

Every time you course-correct AI, ask: **will this come up again?** If yes → add to skills file.

<!-- end_slide -->

What Must Persist (continued)
===

**3. Decision Log**

Architectural decisions with rationale:

```
"2024-03-15: Event-based communication between modules.
 Reason: allows adding modules without modifying existing."

"2024-03-17: Notification preferences in separate table.
 Reason: need to query by preference type."
```

<!-- pause -->

**4. Session Handoff Notes**

At session end: what was done, current state, decisions made, what's next.

<!-- end_slide -->

Team-Level Context
===

All context documents live in the **Git repository**. They're shared artifacts.

<!-- pause -->

Any developer loading the same context gets **consistent AI behavior**.

<!-- pause -->

When one developer updates the skills file, the **entire team benefits**.

<!-- pause -->

This also supports **onboarding** — new or returning developers get full context without verbal handoffs.

<!-- end_slide -->

<!-- jump_to_middle -->

Section 9: When NOT to Use AI
===

<!-- end_slide -->

Skip AI When
===

<!-- incremental_lists: true -->

* The task is **faster to do manually** than to explain
* You're in a domain AI has no context for and explaining takes longer than writing
* You need **novel algorithmic design** requiring deep reasoning about your problem
* You're debugging a **production issue** where speed matters more than process
* The change is a **one-line fix** and you already know the line

<!-- end_slide -->

Be Cautious With AI When
===

<!-- incremental_lists: true -->

* Working with **sensitive data or credentials**
* Making **security-critical** decisions
* AI's suggestions conflict with your team's **architectural patterns**
* You find yourself **accepting output you don't fully understand**

<!-- pause -->

Sometimes writing 50 lines yourself is faster than 30 minutes of prompting and reviewing.

**You have permission to make that judgment call.**

<!-- end_slide -->

<!-- jump_to_middle -->

Section 10: Reference Materials
===

<!-- end_slide -->

Review Checklists Summary
===

| Stage | Key Questions | Time |
|---|---|---|
| PRD | Scope? Assumptions? Actors? Exclusions? Language? | 30-60 min |
| Plan | Architecture? Data model? Dependencies? Interfaces? Edge cases? | 2-4 hours |
| Tests | Match intent? Negative tests? Integration? No hardcoded values? | 20-40 min |
| Code | Matches plan? Conventions? Secure? Input validation? Performance? | 30-60 min |

<!-- end_slide -->

Framework Selection Summary
===

| Factor | B-MAD | Superpowers | GSD | Standard Claude |
|---|---|---|---|---|
| Requirements clarity | High | Medium | Low-Med | Low |
| Documentation volume | Heavy | Balanced | Very Heavy | Minimal |
| Best scope | Large systems | Medium features | Quick MVPs | Small tasks |
| TDD built-in | No | Yes | No | No |
| Review overhead | High | Medium | High | Low |

<!-- end_slide -->

<!-- jump_to_middle -->

Key Takeaways
===

<!-- end_slide -->

Remember These
===

<!-- incremental_lists: true -->

* AI is your **sparring partner**, not your autopilot
* The coding is only as good as your **implementation plan**
* **Front-load review effort** — plan > tests > code
* **30 seconds of constraints** prevents 30 minutes of debugging
* **Revert and regenerate** beats debugging AI's mental model
* **Commit after every module** — Git is your undo button
* **Context files are your memory** — maintain them religiously
* SQA works from the **PRD**, not the code
* One developer, one module, **no handoffs**

<!-- end_slide -->

<!-- jump_to_middle -->

Questions?
===
