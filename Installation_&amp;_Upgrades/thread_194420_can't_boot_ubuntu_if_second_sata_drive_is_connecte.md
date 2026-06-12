---
title: "can't boot ubuntu if second sata drive is connected"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by lime4x4 on 2006-06-11
Current sata drive is partitioned like this 
/dev/sda
partiton 1 is xp
partition4 is ubuntu
swap partition

Don't have a partition 2 or 3

if i have the second sata drive plugged in ubuntu won't boot..Ubunuta is also mounting the xp partition as sda1

If i boot using the recover mode it stops at this point
SD 2:0:0:0 attched scsi removable disk sdc so i'm assuming it's the second sata drive causing the error.. The drive was used in an xp box for file storage no operating system installed on it. As long as i have the drive disconnected it will boot up and run..Any ideas on how to boot with the second drive attached?

---

### Post by elbryan on 2006-06-12
It's a weird thing .. if that would be your secondary sata drive, that could be named sdb not sdc..
I have 2 sata connected and perfectely working .. but I don't have any other scsi device..

You can do 2 thing:
- remove you 3rd SCSI device and trying to use only the 2 hard disk
- going into the BIOS and change the IDE Compatibility Settings that are in Enhanced Mode by default (on my asus mobo) switching on Compatible Mode...

Let me know ..

---

