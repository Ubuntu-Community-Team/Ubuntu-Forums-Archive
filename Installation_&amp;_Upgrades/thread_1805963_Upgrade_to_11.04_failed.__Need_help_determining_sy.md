---
title: "Upgrade to 11.04 failed.  Need help determining system state"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by Bill Roberts on 2011-07-16
I ran the 11.04 upgrade.  At the end, it reported a failure, implied a recovery would occur and the upgrade then finished.  The recovery was supposed to have run sudo dpkg --configure -a.  That does not appear to have happened.  I am concerned that a reboot will render my system inoperative.

Has anyone else experienced a similar issue or have any suggestions?  What information should I provide.  The upgrade did submit a bug report.

---

### Post by jerrrys on 2011-07-17
try it manually.  open a terminal and enter

sudo dpkg --configure -a

---

### Post by Bill Roberts on 2011-07-18
I had already done that and it failed, but I tried again and noticed an error I had missed before.  The build ran out of space in my boot partition.  Unfortunately that leaves the computer without an operating system.  I run a full RAID system that boots from a RAID 1 partition and the upgrade appears to have damaged my arrays beyond recovery.  I was unable to get gparted to boot, so I couldn't make the partition larger (which probably would not have helped anyway).

I am currently installing 11.04 from CD.

I hope the developers understand the problem from the bug report and correct the space management calculations in the install.  It should never have started if there wasn't sufficient space.  I've have space problems before, but they always halted and allowed me to correct the issue.

---

