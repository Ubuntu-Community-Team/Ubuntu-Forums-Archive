---
title: "Ubutnu 7.04 detects onboard Intel video instead of nVidia"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by Versusnja on 2007-10-07
Hi!

I'm trying to install Ubuntu 7.04 Desktop on my XP box.
Each time Ubuntu detects the onboard Inter video card instead of nVidia and then hangs up.

I tried noapci and nolapci parameters, but no luck.

Naturally I disabled the onboard video in BIOS. Yet, the BIOS setting are a bit confusing as there is no "disable onboard video" setting, but "set video priority", which I set to AGI/PCI/onboard. No other settings about video are found in BIOS.

I installed Ubuntu using the alternate CD, but then it freezes with the same problems during the boot time. Same detection problem.

How can I force Ubuntu use nVidia 5700 card instead of onboard Intel?

My box:
P4 3.00GHz
512 RAM
120GB HDD
nVidia 5700

---

### Post by Versusnja on 2007-10-08
**[SOLVED]**: See [this post]("http://ubuntuforums.org/showpost.php?p=3495184&postcount=14").

---

