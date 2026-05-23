# subtitle-formatting-corrector

A Windows utility (C# WinForms) that fixes malformed `.srt` subtitle files where the timestamp format is incorrect and not recognized by media players.

---

## Problem

Some subtitle generators produce timestamps in a broken format:

```
00:01:23.456 -  > 00:01:25.789
```

Instead of the correct `.srt` format:
```
00:01:23,456 --> 00:01:25,789
```

Two issues:
- Arrow style: `-  >` instead of ` --> `
- Decimal separator: `.` instead of `,` for milliseconds

This causes media players to fail to parse the subtitle timing entirely.

---

## What it does

1. Opens an `.srt` file via file browser
2. Scans each line with a regex — detects timestamp lines (contains `->`, no letters)
3. For each timestamp line:
   - Strips all whitespace
   - Removes excessive hyphens
   - Replaces `>` with ` --> `
   - Replaces `.` with `,`
4. Displays the corrected result and overwrites the original file

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | C# |
| Framework | .NET Core 3.1, WinForms |
| Platform | Windows |

---

## Running the project

Open in Visual Studio, build and run. Or run the compiled `.exe` directly from `bin/Debug/netcoreapp3.1/`.
