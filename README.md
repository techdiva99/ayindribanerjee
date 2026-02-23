# ayindribanerjee

## Changelog

- 2026-02-23: Added GA4 tracking (`G-K1HCBV2XRR`) on `index.html` and `contact.html`, including custom event instrumentation and documentation.

## Google Analytics (GA4)

This site uses GA4 with Measurement ID: `G-K1HCBV2XRR`.

Tracking is installed in:
- `index.html`
- `contact.html`

## Custom Events

### index.html
- `contact_navigation_click`: user clicks a link to `contact.html`
- `outbound_click`: user clicks an external link
- `newsletter_subscribe_submit`: newsletter form submission

### contact.html
- `contact_form_submit`: contact form submission
  - Parameters: `event_type`, `has_location`
- `back_to_speaker_click`: user clicks link back to `index.html`
- `outbound_click`: user clicks an external link

## Event Naming Convention

Use lowercase snake_case for all GA4 custom events:
- Pattern: `<area>_<action>_<object>`
- Examples:
  - `contact_navigation_click`
  - `newsletter_subscribe_submit`
  - `contact_form_submit`

Parameter naming:
- Use lowercase snake_case keys (for example: `event_type`, `has_location`, `link_url`).
- Keep parameter names stable over time to preserve report consistency.
- Prefer short, descriptive values (for example: `Virtual`, `In-person`).

## New Event Checklist

When adding a new GA4 event:
1. Pick an event name using the convention: `<area>_<action>_<object>`.
2. Add tracking in the relevant page script (`index.html` or `contact.html`) with `gtag('event', ...)`.
3. Include only useful parameters, with snake_case keys.
4. Verify in GA4 DebugView and Realtime after deployment.
5. Document the event and parameters in this README under **Custom Events**.

## Validation

After deployment:
1. Open GA4 Realtime.
2. Visit the website and perform a few actions (click links, submit forms).
3. Confirm events appear in Realtime and DebugView.

## Analytics Operations

### Weekly cadence (30 minutes)
1. Traffic pulse (5 min): compare users/sessions vs previous week.
2. Funnel health (8 min): check `homepage -> contact_navigation_click -> contact_form_submit`.
3. Channel quality (7 min): compare `contact_form_submit` by source/medium.
4. Intent mix (5 min): review `event_type` trend (`Virtual` vs `In-person`).
5. Action log (5 min): capture 1 insight and 1 action for the week.

### Decision rules
- If homepage traffic is high but `contact_navigation_click` is low: improve homepage CTA copy/placement.
- If `contact_navigation_click` is high but `contact_form_submit` is low: simplify contact form messaging and trust cues.
- If a source/medium drives higher inquiry rate: increase effort/content in that channel.