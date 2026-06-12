---
title: "Invalid partition [Resolved]"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by David_UK on 2007-01-13
Hi

As a very new user of 6.06 I want to get familiar with the install and (dare I say it), *uninstall* of ubuntu.
I have an old test-rig for playing about: HDD 1 with original win98se OS, and HDD 2 with 6.06.  The dual boot works fine.
For the purposes of education, I want to replace the MBR with the original windows one (as if removing linux & stopping dual boot) and then modify that MBR to enable dual-boot again.

In DOS, I use a win98 startup floppy and: [fdisk /mbr] but it fails with the error: "C drive does not contain a valid FAT or FAT32 partition".  Despite this, I can boot to windows just fine.

The only cause I can think of is, I did use GParted to resize the windows partition on HDD 1 (then I decided to install linux on a separate HDD instead).  Might this have made the partition unreadable to DOS?

Any comments gratefully received.

---

### Post by David_UK on 2007-01-14
Ok, I found the solution.  Either a dodgy connection or a fault with the IDE cable to the HDD's.  I've changed that and DOS fdisk can now 'see' the partitions.

---

### Post by Sef on 2007-01-14
Thank you for letting us know that your resolved your problem and congrats on solving it.   If you have any more questions, please ask.

---

