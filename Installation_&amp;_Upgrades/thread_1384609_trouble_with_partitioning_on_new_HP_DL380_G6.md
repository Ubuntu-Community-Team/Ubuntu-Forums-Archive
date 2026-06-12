---
title: "trouble with partitioning on new HP DL380 G6"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by lywellyn on 2010-01-18
I'm having trouble installing Ubuntu on a brand new HP DL380 G6 server. Any time I go through the install, it freezes at 33% of formatting the first partition. I have tried 9.04 server disk, 9.10 server disk, and 9.10 desktop (all AMD64). I'm running out of ideas to troubleshoot. The server is listed as supported by Ubuntu 9.04. Here's more of the hardware:
 
2x quad-core Intel Xeon X5550 procs
16GB of RAM
5x 300GB SAS drives in RAID-5 array (1.2TB useable)
 
I just finished installing with the 9.10 alternate install disk (AMD64), and after reboot, it doesn't seem to find the boot partition and just sits there after attempting to boot from CD and hard disk.
 
This is getting very frustrating. Spent nearly the whole workday on this. Please help!

---

### Post by lywellyn on 2010-01-19
Also, found out the array controller is an HP Smart Array P410i. I think the main issue may be a problem with grub at this point, so I'll be attempting to install grub again.

---

### Post by lywellyn on 2010-01-19
Found the solution with some help from Canonical. With this particular RAID controller, you have to enable the drive caching option after creating the array. If you do not, the install hangs and you cannot get a stable install. Good luck for anyone who benefits from this info.

---

