---
title: "Sound plays X shows blank screen (install)"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by lot3k on 2006-09-27
I've reburned the 64bit CD 3 times, ran tests for corruption.  Checked kernel init strings for issues, flipped resolutions around, and attempted to load CD in safe mode.


AMD X2 3800
Geforce 7800GTS (SLI)
2x512MB ram (all checks out)
SBLive 5.1 & X-FI (come on 2nd quarter 2k7)

I'm wanting to test Ubuntu, considering switching from gentoo.  Any help would be appreciated, I will try to get any debug info to anyone if it will help, doesn't seem there is much information I can gather though from this process.  I heard mention of an alternate install, is that functionality built into all CDs, or are there seperate ISOs I need to grab.


Thanks in advance.

---

### Post by lot3k on 2006-09-28
anybody?

---

### Post by ryboto on 2006-09-28
this sounds like the exact same issue I'm having.  I initially downloaded the 64bit desktop install, but before the install even begins, my monitor loses signal, and i hear an ubuntu welcome sound, or so I assume that's what it is.  So, the systems still running, I just have no display.  I just tried the alternate disc, and it installed, but when I restarted and tried to log in for the first time, the same thing happened.

---

### Post by lot3k on 2006-09-29
Yea, I managed to get it installed.  Too restrictive, but a beautful distro none the less.

---

### Post by ryboto on 2006-10-01
how did you get the blank screen to go away?

---

### Post by empthollow on 2006-10-01
i had a similar problem with x86 version. i had to change lower the vertrefresh line in /etc/X11/xorg.conf

---

