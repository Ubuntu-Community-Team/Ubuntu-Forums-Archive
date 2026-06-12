---
title: "Second hdd not visible."
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by David B on 2011-01-16
Hello,

I have win 7 installed on my main first hdd and would like to install
ubuntu 10.10 on my newly installed second hdd. Problem is that during install
when i choose manual partitioning my second hdd is not visible. So it is impossible
to choose the disk for installation. 
Tried to disable first hdd in bios but pc than fails to boot from dvd.
Tried the alternate ubuntu cd and second drive even then is invisible.
Second hdd is visible in win 7 and fully can be manipulated in 7.
Tried to format the drive as fat32, ntfs, linux ext 2 and 3, but same problem.
Drives are mounted as 1st hdd is primary master and 2nd hdd is secondary master.


How can i resolve this problem?

---

### Post by dino99 on 2011-01-16
check the hdd bios settings, is it a sata ? Might be set as Compatible or ahci

boot on livecd, open a terminal and run:

sudo dmraid -rE

---

### Post by David B on 2011-01-16
The drive is IDE. 
  output of sudo dmraid -rE


= no raid disks

---

### Post by David B on 2011-01-17
In gparted second hdd is still invisible

Any suggestions to solve this problem ?

---

