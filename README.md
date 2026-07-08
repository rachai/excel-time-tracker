# ⏱ Excel Time Tracker

A simple, self-contained time tracker that lives entirely in an Excel workbook. Click one button to start, click it again to stop, and your hours are logged automatically — no accounts, no subscriptions, no cloud.

## Why this exists

I built this because the online time-tracking software I used to rely on decided to **put Excel export behind a paywall** — a feature existing users like me had always had for free. I didn't want to pay a subscription just to get my own hours out of a spreadsheet, so I made a tracker where the spreadsheet *is* the product. Your data is yours, it stays on your machine, and exporting is just… saving a file.

It's free and open source so nobody has to deal with that again.

## Features

- **One-button timer** — the Start button turns into a red Stop button while a timer runs.
- **Live status** — see what you're currently tracking and a running elapsed clock.
- **Projects & clients** — keep a project list; the client fills in automatically. You can also create a new project on the fly when starting a timer.
- **Automatic math** — Duration and Hours are calculated from your Start/End times.
- **Resume** — start a fresh entry that reuses a previous entry's project and description.
- **Reports** — generate a filtered, sorted summary for any date range in a new workbook.
- **No lock-in** — it's a plain `.xlsm` file. Your data never leaves your computer.

## Requirements

- **Microsoft Excel for Windows (desktop).** The buttons use VBA macros with pop-up forms (UserForms), which run only in desktop Excel on Windows. Excel on Mac and Excel on the web will show your data but the buttons won't work.

## ⚠️ About the "security risk" warning

When you first open the file, Excel will probably show a pink/red bar saying **"SECURITY RISK — Microsoft has blocked macros from running because the source of this file is untrusted."**

**This is expected and normal — don't be alarmed.** Any `.xlsm` file downloaded from the internet gets this treatment from Windows/Excel automatically, regardless of what's actually in it. It's not a sign that anything is wrong with this file specifically. Since this project is open source, you (or anyone) can open the VBA editor (**Alt+F11**) and read every line of macro code yourself before enabling anything, if you'd like to verify what it does.

To make the warning go away for good, follow the first-time setup below.

## First-time setup (important!)

Because this file contains macros and was downloaded from the internet, Windows blocks it by default. Do this **once** after downloading, *before* you open it:

1. **Unblock the file.** In File Explorer, right-click `Time tracker open source.xlsm` → **Properties** → at the bottom of the **General** tab, check the **Unblock** checkbox → **OK**.
2. **Open the file** in Excel.
3. If you still see a yellow **SECURITY WARNING** bar saying macros are disabled, click **Enable Content**. (You shouldn't see the red "security risk" bar at all if step 1 was done first.)

If you skip step 1, the buttons will silently do nothing — that's the most common "it's not working" issue. If you already opened the file and saw the warning, just close it, do step 1, and reopen it.

## How to use it

### 1. (Optional) Set up your projects
Go to the **Projects** sheet and list your projects and their clients (Notes are optional). These auto-fill the Client column on the tracker. You don't have to do this first — you can also create a project the moment you start a timer.

### 2. Start a timer
On the **Time Tracker** sheet, click **▶ Start Timer**. You'll be asked to:

1. **Pick a project** from the pop-up — or type a new name to create one (it'll ask for the client and add it to your Projects list).
2. **Enter a description** — this is required; the timer won't start without it.

A new entry is added at the top of the list with today's date and the current start time, and the button turns red: **■ Stop Timer**.

### 3. Stop the timer
Click the red **■ Stop Timer** button. It stamps the End time and fills in the Duration and Hours for that entry, then turns blue again.

> Only one timer runs at a time. The button always acts on the currently running entry.

### 4. Resume a previous entry
Click **⟳ Resume entry** to start a **new** timer that reuses the project and description of an entry you pick from the list. (This is disabled while a timer is already running — stop the current one first.)

### 5. Create a report
Click **📄 Create report** and choose a period:

- **1 = Last month** (the previous full calendar month)
- **2 = Last X days** (you enter the number of days)
- **3 = Custom range** (enter start and end dates as `yyyy-mm-dd`)

The matching entries are pulled into a **new, unsaved workbook** called "Time Report," sorted by Client → Project → Description (and newest date first). Use **File → Save As** to store it wherever you like.

### Columns explained

| Column | What it is |
|---|---|
| Description | What you worked on (required at start) |
| Project | Chosen or created in the start pop-up |
| Client | Auto-filled from the selected Project |
| Date | Filled with today's date when you start |
| Start / End | Timestamps (filled by the buttons) |
| Duration | End − Start (calculated) |
| Hours | Duration expressed as decimal hours (calculated) |

## Exporting your data

It's already a spreadsheet — just **Save As** and choose `.xlsx`, `.csv`, or whatever you need. Reports also open as their own workbook ready to save. That's the whole point. 🙂

## Troubleshooting

- **Buttons do nothing** → You skipped the Unblock step, or macros are disabled. See First-time setup.
- **I see a red "SECURITY RISK" bar** → This is normal for any downloaded `.xlsm` file, not specific to this one. Close the file, do the Unblock step above, then reopen it.
- **Still no macros** → File → Options → Trust Center → Trust Center Settings → Macro Settings → enable macros (or add the folder as a Trusted Location).
- **Nothing happens on Mac / Excel Online** → The pop-up forms need desktop Excel on Windows.
- **Client doesn't auto-fill** → Make sure the project exists on the Projects sheet, spelled the same way.

## License

Released under the GNU General Public License v3.0 (GPLv3) — free to use, modify, and share. Anyone who distributes a modified version must also keep it open source under the same GPLv3 terms, so it can never be turned into closed, proprietary software. See the LICENSE file.
