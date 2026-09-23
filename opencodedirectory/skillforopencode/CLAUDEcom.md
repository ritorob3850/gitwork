# Chrome Search - Quick Reference

## To search for anything, ask:

"Execute the chrome search script for [topic]"

Or directly:

"Run: & "D:\claude\windowsautomation\.claude\skills\chrome-search\scripts\search_chrome.ps1" -SearchTerm "TOPIC""

## Examples:

- "Execute the chrome search script for kubernetes"
- "Search for Python tutorials using chrome"
- "Look up Docker documentation"

The script will:
1. Ask for approval
2. Run the PowerShell script
3. Open Chrome with results

---

# WhatsApp Search - Quick Reference

## What it does

Reads the latest message from WhatsApp Web (via Chrome DevTools Protocol), then uses it as a search query in Chrome.

## Prerequisites

Chrome must be started with remote debugging enabled:

```
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=9222
```

Then open https://web.whatsapp.com and log in.

## To use, say:

"Read my WhatsApp message and search for it"

Or directly:

"Run: & "D:\claude\windowsautomation\.claude\skills\whatsapp-search\scripts\read_whatsapp.ps1"

Then chain the output to the chrome-search script:

"Run: & "D:\claude\windowsautomation\.claude\skills\chrome-search\scripts\search_chrome.ps1" -SearchTerm "<MESSAGE_TEXT>""

## Auto-search from Bubul2

When Bubul2 sends a message starting with **"search"** (e.g. "search kubernetes tutorial"), run:

```
& "D:\claude\windowsautomation\.claude\skills\whatsapp-search\scripts\bubul2_watch.ps1"
```

This script:
1. Checks if Chrome is running with remote debugging
2. If not, launches Chrome + WhatsApp Web and asks you to log in
3. Reads Bubul2's latest message
4. If it starts with "search", extracts the term and opens Chrome with results
5. If no "search" command, just shows the message

To just peek at Bubul2's last message without searching:

```
& "D:\claude\windowsautomation\.claude\skills\whatsapp-search\scripts\check_bubul2.ps1"
```

---

# Available Skills

The following skills are available in `D:\claude\windowsautomation\.claude\skills\`:

- **chrome-search**: Opens Chrome to Google search for a term
- **whatsapp-search**: Reads latest WhatsApp Web message from Chrome via CDP
