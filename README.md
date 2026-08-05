# Weekly Study Timetable

A simple, week-structured JSON timetable — built from a daily alarm schedule that repeats every day — plus the [Right Now](./right-now.html) app that displays whatever task is currently active and switches automatically as the time crosses into the next slot.

## Files

| File | Purpose |
|---|---|
| `schedule-week.json` | The timetable, one array per day of the week |
| `index.html` | Single-file app: local passcode login, full-screen "current task" display, editable timetable, CSV/Excel/TXT/JSON import |

## JSON structure

```json
[
  {
    "time": "07:00",
    "label": "Wakeup"
  },
  {
    "time": "09:30",
    "label": "Label 1"
  },
  {
    "time": "12:30",
    "label": "label 2"
  }
]
```

- Top-level keys are the seven days of the week, capitalized (`Monday` … `Sunday`).
- Each day holds an array of items sorted by time.
- `time` — 24-hour `HH:MM`.
- `label` — the task name, title-cased (e.g. `Core One`, `Current Affairs`, `UP GK Book + Answer Writing`).

The current data repeats the same nine daily blocks across all seven days, since the source alarms were set to "every day." Edit any day's array independently once your weekday and weekend routines diverge.

## Using it with Right Now

`index.html` currently reads a **flat array** (`[{ "time": ..., "label": ... }, ...]`), not a week-keyed object. To load one day from `schedule-week.json`:

1. Open `index.html`, tap the ✎ (edit) icon.
2. Tap **Paste text**, or **Upload CSV / Excel / TXT / JSON**.
3. For JSON upload, copy just one day's array out of `schedule-week.json` (e.g. the `"Monday"` value) into its own `.json` file — `[{ "time": "09:00", "label": "Core One" }, ...]` — and upload that.

Everything the app stores (passcode, schedule) lives only in that browser's `localStorage` — no server, no account.

## License

Personal use — adapt freely.
