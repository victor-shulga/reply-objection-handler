# reply-objection-handler

Viktor Shulha's **per-reply engine** for B2B outbound — a Claude Code plugin (skill).

Paste **one** thing — an inbound reply, an objection, a screenshot of a thread, a ghosted
conversation, a lost-proposal note, or a public post that asks for help — plus a little context, and
it returns the single best next message, **ready to send in the prospect's language**.

It is the **surgeon** for one thread. For batch analysis of many replies at once, use `reply-audit`
(the epidemiologist). They feed each other: audit findings become rules here; replies written here are
tagged so the next audit aggregates cleanly.

## What it does

1. **Reads** the thread (who, title, company, channel, what we sent, the exact reply).
2. **Classifies** on two axes that are never collapsed — **sentiment** (state of the lead) +
   **objection type** (the reason) — the same taxonomy as `reply-audit`.
3. **Routes** to the right play.
4. **Writes** ONE ready-to-send reply / follow-up + Next Action + CRM tag.

### Covered reply types
`HOT / INTERESTED` (lock the meeting) · `HOT — FUMBLED` (friction-free recovery) · `WANTS_PROOF` ·
`SOFT_NO` · `TIMING / TOO_BUSY` · `INCUMBENT / IN-HOUSE` (overflow angle) ·
`CHANNEL / ROUTING` ("we buy through our A/E or CM") · `WRONG_PERSON` · `WRONG_GEO` ·
`WRONG_ICP` · `DEAD_DATA` · `CURIOUS_PROBING` · `HARD_NO / OPT-OUT`.

### Covered follow-up scenarios
Ghost bumps (new angle each time) · value-first re-engage (research-grounded) · trigger-based
(work anniversary, funding, new role) · lost-proposal follow-up (one-letter feedback + bench flag) ·
inbound-trigger cold message (reply to a post that asks for help — comment-first, then DM).

## The constitution (core rules)

- Reply in the **prospect's language**.
- **One reply per objection** — ignored → change angle or close gracefully.
- **Lead with value; never pitch into an objection.**
- **Never end passive** ("let me know if you change your mind"). End with a question, a specific date,
  an easy binary, or a graceful close.
- Objection replies **< 80 words**; value-first messages may be longer *only if* they deliver substance.
- **Hot lead = confirm THEIR time & format** — no upsell, no format swap, no friction stack until booked.
- **Channel / geo / referral objections are a MAP, not a NO** — extract the next target or person.
- **Hard-no / opt-out = drop instantly.**

## Structure

```
skills/reply-objection-handler/
  SKILL.md        # router + 13-type taxonomy + constitution + output format
  templates.md    # growing repository of proven, harvested reply templates
```

`templates.md` is the **compounding asset**: when a new pattern is solved, the winning template is
appended (with the client/context it came from).

## Install

Add as a marketplace plugin, or symlink the skill into `~/.claude/skills/`:

```bash
ln -s "$(pwd)/skills/reply-objection-handler" ~/.claude/skills/reply-objection-handler
```

## Validate

```bash
bash scripts/validate.sh
```

MIT © 2026 Victor Shulga / B2B Global
