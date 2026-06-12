---
title: "Kernel upgrade problem -14 to -20"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by djenner on 2010-04-10
Oh, last week or thereabouts, the automatic upgrades included a kernal upgrade from 2.6.31-14 to -20.  -20 fails to load, reports a panic trying to address a particular file system block or something (sorry, over my head here).  This is a WUBI-installed 9.10 installation, works quite well for my purposes with the slightly older kernel, and I am able to boot in since I am offered a menu with both kernel options.

But [LIST]
[*]it would be so nice to edit that menu to eliminate the -20 kernel option (so that it won't automatically try to boot that and fail).
[*]It would be nice to kill that -20 kernel altogether.
[*]It would be really nice to understand the problem and fix it.
[/LIST]

Effective guidance (not over-technical please; I am old enough that is merely confuses me...) on any or all of these would be most welcome.

---

### Post by shaka_zulu on 2010-04-10
If i have understood you correctly you had an upgrade which had brought new Kernel 2.6.31-20 and when you reboot computer it doesn't want to boot that new Kernel because this is broken? Right? Do you have Ubuntu, Kubuntu or something third?

---

