---
title: "Dual boot install w/ XP and Ubuntu"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by sully1109 on 2007-03-04
I am trying to set up my pc as a dual boot machine running XP sp2 and Ubuntu 6.10. XP is already installed on the c: partition of my 1st HD, and I have a d; partition formatted in NTFS that I would like to install Ubuntu on. When I partioned it using the gparted utility during Ubuntu install, it appeared to work ok but then told me that I did not have a root directory specified, which I did. i exited the install and upon reboot XP would not launch, just got a message about inserting a disk and hit any key to reboot. So I had to restore everything from my backup. Partioning a partition that does not have anything on it shouldn't effect the entire system, right?

---

### Post by Kateikyoushi on 2007-03-04
Right, it shouldn't have done anything to the other partitions. Try to run a checkdisk in windows to see if everything is ok with the drive.

---

