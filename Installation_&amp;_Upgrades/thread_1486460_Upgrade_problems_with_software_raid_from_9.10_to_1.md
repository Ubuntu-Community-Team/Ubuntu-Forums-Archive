---
title: "Upgrade problems with software raid from 9.10 to 10.04"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by tpoindex on 2010-05-17
I have recently upgraded one of my machines from 9.10 o 10.04, and while the upgrade itself was complete flawless, I experiences problems while booting after the install.  

My configuration includes software RAID-1 devices /dev/md0 and /dev/md1 for /home and /extramd, which I have had partitioned and mounted since 8.04.  In each previous upgrade, I experienced no problems with mounting these partitions after the upgrade.  After my most recent upgrade to 10.04, my two RAID-1 md devices were not mounted at boot time.  The boot splash screen had a cryptic message of "Continue to wait; press 'S' to skip; press 'M' for maintenance mode"  (or similar.)  Eventually, I could either 'Skip' or drop into maintenance mode, and the problem would disappear, allowing me to continue booting.

After perusing some other like upgrade problems, I installed the 'dmraid' package ("sudo apt-get install dmraid").  This installs an init.d script to run "dmraid -ay" at boot time, and fixed my problem.

---

