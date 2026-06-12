---
title: "RAID information Needed HELP!!"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by riscostm on 2006-10-10
Hello,  Please can I have some advice on setting up a Raid Ubuntu server. :idea: 

Hardware Spec

File Server
P4
512mg
Adaptec Serial ATA II RAID 1420SA (Drivers ??)(Which drivers can I use with Ubuntu)
2x 500GB Drives setup on a RAID configuration 	\\:D/ (Will be large files)
Ubuntu Lamp Server (With a local intranet)

What would be the best filing system etc..

Cheers,
Johno

---

### Post by bdb on 2006-10-13
What type of RAID (0,1,5....)?

You do not need drivers to set up the (software) raid.  If ubuntu recognizes your hard drives that is good enough.

Try using the alternate-dapper install.  This has more options for partitioning.  If  you are setting up RAID 0, at least your boot partition needs to be RAID 1.  Otherwise grub installation will fail.

---

