---
title: "Intel graphics chip and suspend"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by pinegreen on 2007-10-28
Hi,

I had a problem on my X40 suspending with compiz on gutsy - one recovery the screen was just really corrupted and nothing helped, I had to restart gdm. Just sharing this in case people have similar problems: I couldn't find anything on the web.

After 4 days of faffing around and changing the acpi-defaults file I found the right solution: change driver in xorg.conf from intel back to i815. Now it works fine, although goodies of the new intel driver are lost, I guess...

---

### Post by brandon30x on 2007-10-28
I also have intel graphics and had a problem with suspending: [http://ubuntuforums.org/showthread.php?t=590194]("http://ubuntuforums.org/showthread.php?t=590194") Upon resuming my screen would be blank, and I had to kill the x server (although it was not locked up, just allways had a black screen.) I never tried the i810 driver and my solution was to disable desktop effects (compiz)

-Brandon

---

