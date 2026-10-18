ROLE
You are a front-end prototyper building a low-fidelity, clickable prototype of "Juno PM: Backlog De-noiser," an internal tool for RocketShip, a B2B SaaS platform for enterprise data teams. The user is a Product Manager who needs to see which untouched Jira tickets are really the same problem, and which deserve attention this week. Juno is an AI Associate PM: it reads, clusters, and proposes. It never changes anything.

TASK
Build a single-page web app that shows a weekly digest of clustered backlog tickets.

1. Header: title "Backlog De-noiser", status labels "RECOMMENDATION" and "DRAFT", and a visible banner: "Low-fidelity prototype, SAMPLE DATA. Nothing here was read from a real Jira, Slack, or Notion workspace."
2. Bottom-line box at the top: one or two sentences summarizing how many tickets collapse into how many problems, and which clusters need a human this week. Under it, a small line: "Confidence: Medium overall. Why I created this: weekly digest trigger; it supports sprint-planning decisions."
3. A toggle to rank clusters by "Breadth (distinct customers)" or "Exposure (renewals, strategic accounts)". Re-sort the list when toggled.
4. A ranked list of 5 clusters. Each collapsed card shows: rank, cluster name, ticket count, distinct customers, segment mix, oldest ticket age in days, trend (Growing / Stable / Unclear), and a confidence pill (High / Medium / Low).
5. Clicking a card expands it to show:
   - "Why it ranks here" (one or two sentences) plus renewal exposure
   - Evidence table with Jira keys (e.g., RS-1042) and a Slack thread reference
   - "Proposed duplicate merges": each row says "RS-1188 → merge into RS-1042" with a short reason and Approve / Reject buttons. After clicking, replace the buttons with "Approved by PM (draft only, no Jira change made)" or "Rejected by PM (...)".
6. Use this sample data (all placeholders, label every ticket key and thread as sample):
   - Cluster 1: "CSV export times out on large pipelines", 14 tickets, 6 customers, 4 Enterprise + 2 Mid-market, oldest 94 days, Growing, High confidence, 2 renewals within 90 days. Merges: RS-1188 into RS-1042 (same error text), RS-1203 into RS-1042 (same report, reworded).
   - Cluster 2: "Lineage graph drops columns", 11 tickets, 8 customers, oldest 140 days, Stable, Medium, no renewals within 90 days. Merge: RS-0931 into RS-0877.
   - Cluster 3: "Slack alert notifications delayed", 9 tickets, 5 customers, oldest 61 days, Stable, Medium, 1 renewal within 90 days. Note: root cause is a hypothesis, not confirmed.
   - Cluster 4: "SSO login loop for Okta tenants", 5 tickets, 2 strategic Enterprise customers, oldest 18 days, Growing, High, 1 renewal within 30 days. Show a red banner inside the card: "ESCALATE to named human: authentication / access issue with renewal exposure. Rule triggered: P0-adjacent." No merge buttons.
   - Cluster 5: "Dashboard sharing permissions unclear", 4 tickets, 3 customers, oldest 33 days, Unclear, Low confidence. Show an amber banner: "NEEDS CLARIFICATION: two tickets report a bug, two may describe intended behavior. Missing: the product spec for sharing roles."
7. Footer: "Decision needed: which clusters enter next sprint planning, and approve or reject the proposed merges. Juno has changed nothing in Jira. Owner: owning PM (fallback: PM lead)." Under it, a short self-check list: answer first, every claim sourced, inside autonomy limits, confidence stated.

CONSTRAINTS
- No backend, no login, no real API calls. Hard-code the sample data in the front end.
- Never invent customer names. Show customers only as counts.
- Every claim shows a Jira key or Slack thread reference, all clearly marked as sample.
- Approve/Reject buttons only change on-screen state. Nothing sends, publishes, or edits anything.
- Cluster 4 (authentication) must always show the escalation banner and must not show action buttons.
- Cluster 5 must always show the NEEDS CLARIFICATION banner.
- Both ranking views must be available so high-ARR accounts don't automatically outrank widespread issues.
- Low fidelity only: no charts, no animations, no images. Plain cards and tables.
- Works on mobile and desktop, supports light and dark mode.

FORMAT
- One page, structured top to bottom: banner, bottom line, ranking toggle, cluster cards, footer.
- Bottom line first, decision needed last.
- Clean neutral styling: system font, off-white background, one accent color (indigo), colored pills for confidence (green High, amber Medium, red Low).
- Cards collapsed by default; expand on click.
- Keep all text short and scannable.
