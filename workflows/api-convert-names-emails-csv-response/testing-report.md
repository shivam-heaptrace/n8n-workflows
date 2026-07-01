# testing-report.md — API - Convert Names Emails - CSV Response

## Summary
| Test Type | Result |
|---|---|
| Happy path | ✅ Pass |
| Error handling | ✅ Pass |
| Edge cases | ✅ Pass |

## Test Method
User tested directly in n8n by activating the workflow and sending a POST request to the webhook endpoint with a JSON array of contact objects. Claude confirmed test result via user report in chat.

## Happy Path Test
**What was tested:** A POST request was sent to `/webhook/names-to-csv` with a JSON array containing multiple objects each with `name` and `email` fields.
**Outcome:** The workflow returned a `text/csv` response with a correctly formatted CSV string containing a `name,email` header row followed by one quoted row per contact.

## Error Handling
**Error triggered:** Payload with an empty array or unrecognised structure submitted.
**Expected behaviour:** Workflow returns a CSV response with an empty `csv` field and an `error` message describing that no valid array was found.
**Actual behaviour:** ✅ Matched — the Code node gracefully handles missing or empty input and returns a safe fallback rather than failing the execution.

## Edge Cases Tested
| Scenario | Result |
|---|---|
| Name or email containing double-quote characters | ✅ Quotes correctly escaped as `""` in the CSV output |

## Test Environment
- **Mode:** Live (user-executed in n8n directly)
- **Test date:** 2026-06-19
- **Tested by:** Vishal Mishra
- **n8n Workflow ID:** 2DEXfAJcznLM2f5j
- **Registry ID:** 2c14d702-cdb7-4f44-9b23-f3c5527ed84d
- **COE Portal:** https://coe-portal.ai.fulcrum.tools/catalog/2c14d702-cdb7-4f44-9b23-f3c5527ed84d
- **Instance:** fulcrumtest.app.n8n.cloud