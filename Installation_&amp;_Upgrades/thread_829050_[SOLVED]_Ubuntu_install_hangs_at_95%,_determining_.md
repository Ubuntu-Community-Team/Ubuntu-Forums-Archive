---
title: "[SOLVED] Ubuntu install hangs at 95%, determining packages to uninstall"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by daveerickson on 2008-06-14
Alright, here is the deal. I have been converting my friends and family over to Ubuntu for about the past year. Working on my sisters desktop I ran into an install problem that I had never seen before, and after monkeying around I came up with a "fix" in a sense that it doesn't hang any longer, not that I fully understand why. I figured I'd post what I did in case it helps someone else out.

As the title says, the install would freeze. Not just the intaller, the whole pc. I couldn't move the mouse, turn num lock on or off, hard locked. The only solution was to hit the reset button. I had played around with the noapic stuff with no luck. Then a perused through the bios setting and found the setting "APIC Mode" was set to Disabled. I changed it to Enabled and that seemed to do the trick. I thought it strange that Linux would not be able to detect the correct setting and use the correct mode, but I was relieved that this worked.

This specs are as follows if it makes any difference for anyone:
Shuttle SN45G case/mobo
Athlon XP 2100+
512 MB RAM
Radeon 9600 AIW AGP card
200GB HD

I am curious if anyone else has had a similar issue/fix, and if anyone could explain why it now works. I would love to further my Linux knowledge. Thanks. :)

---

