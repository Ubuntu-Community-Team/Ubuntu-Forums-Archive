---
title: "Problem with my intel video card and the 9.1 version"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by gwu777 on 2009-11-13
Hi there,

I have been trying to make my laptop work with ubuntu 9.04 and 9.1 for month. Apparently, there is a problem with the video card which is not compatible.

I have a samsung V25 Pentium 4 2.4gh with 512Mb memory. it has an Intel 845GV IGD onboard card.

Everytime I tried to make a clean install from CD ( I have tried every CD, live/alternate) I never manage to install 9.04 successfully, the only thing I ever got was a blank screen despite A LOT of tinckering. I managed to install 9.10rc after playing around a lot, but honestly, the system was never stable, it regularly hanged, I got a blank screen on startup 1 out of 3 times it started (I never worked out why...)

Out of desperation I have reinstalled 8.04, which is now upgrading to 8.1. It works very well, I even have compiz running!

Here is my question, knowing that I never managed to install from a CD version 9, should I try to do the upgrade, or should I stay with my working 8 version?

I hope what I say make sense, any comment would be verymuch appreciated...

---

### Post by tommcd on 2009-11-13
> **gwu777 said:**
> 
Here is my question, knowing that I never managed to install from a CD version 9, should I try to do the upgrade, or should I stay with my working 8 version?

If it were me, I would do a clean install of Ubuntu 9.10. Use the final version, not the RC. I would do it from the alternate CD, since I have found that this is the most fail safe method of installing. You can use the live CD if you want though.
The intel driver in 9.04 had a lot of problems due to massive changes upstream in the intel driver and kernel mode setting. The situation is much improved in 9.10.
The problems with the intel driver were not present in 8.04 and 8.10.
To upgrade from 8.10 to 9.10, you would need to upgrade from 8.10 to 9.04 to 9.10. You can not skip versions when upgrading. The only exception is going from one LTS version to the next LTS version.
A clean insall of 9.10 would likely be faster and easier than upgrading from 8.10 > 9.04 > 9.10.

---

