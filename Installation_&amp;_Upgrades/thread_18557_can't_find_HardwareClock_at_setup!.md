---
title: "can't find HardwareClock at setup!"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by zack18 on 2005-03-07
Hi all,

when starting up my computer, i notice that ubuntu *failed* to locate the hardware clock (in order to update the system clock).  

it says it does NOT have access to the hardware clock.

it says to use the --debug option to see the details of our search for synchronizing  clock.  (there is no "hwclock --debug option) and no hits when i man --debug).

the clock located that the top right hand corner of my screen is correct, i'm confused.

after reading some files, i know i'm not suppsed to use "hwclock" to set or update the hardware clock but i should use "ntp" for ubuntu's debian based OS.  however, i don't have ntp installed on my computer and i don't even know if this is the issue.

any suggestions or additional items i might check.

---

