# OALUG Website — Agent Instructions

## Structure

Single-page static site deployed via GitHub Pages. All meetings live in one file:

| File | Purpose |
|---|---|
| `meetings-data.js` | **Single source of truth.** `allMeetings` array — all meeting data for both pages. |
| `index.html` | Home: announcements + upcoming meetings (splits `allMeetings` by date). |
| `past-meetings.html` | Past meetings grouped by year (splits `allMeetings` by date). |
| `styles.css` | Styles. |
| `banner.png`, `banner2.png` | Images. |

## Adding / Updating Meetings

Add entries to `allMeetings` in `meetings-data.js` (ascending date order). Both pages auto-filter by comparing dates against today. Format:

```js
{ date: 'YYYY/MM/DD', time: '6:30 PM', location: '...', topic: '...', description: '...', calendarLink: '...' }
```

- `date` must use `YYYY/MM/DD` (the date parser depends on this).
- `calendarLink` is optional; omit for meetings without a calendar invite.
- Use HTML in `location` and `description` — the pages render them via `innerHTML`.
- Comment out meetings that have passed instead of removing them.

## Style

- Inline styles only where necessary (e.g., `past-meetings.html` sidebar).
- Prefer `styles.css` for all other styling.
- No build step, no linter, no test framework.
