---
title: "Intel Driver 2.12 82865G"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by jordaavies on 2010-08-07
****Hi, not a major problem but I'd really like to get a fix.
I have intel 82865G card, which was working perfectly until I found the intel driver 2.12 and upgraded it without really thinking. Now I have no visual effects or compiz, I can enable them but the whole GUI whill flicker or disappear. Can I downgrade the driver (and how?) or do I leave it for a upgrade fix?

Thanks.

---

### Post by rcchume on 2010-08-07
[FONT="Arial"][SIZE="1"]
Check if this helps with the flicker problem:

Run ccsm by going going to [System -> Preferences -> CompizConfig Settings Manager]. Click on the "General Options" button under the "General" header and then go to the "Display Settings" tab.

Untick the "Detect Refresh Rate" option, change the "Refresh Rate" number to the one of your monitor, and then tick on the "Sync to VBlank" option. If you don't know your monitors refresh rate, then go to [System -> Preferences -> Display] and check the "Refresh rate:" drop-down.[/SIZE][/FONT]

---

### Post by jordaavies on 2010-08-07
thanks for replying, but no change :( its like I choose normal effects, then it searches for available drivers, then the windows move slightly to refresh and become invisible, I get them back by using expose to find the buttons to revert back, menus dont show up either.

---

