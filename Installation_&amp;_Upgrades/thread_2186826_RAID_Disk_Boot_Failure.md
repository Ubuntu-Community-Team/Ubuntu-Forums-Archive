---
title: "RAID Disk Boot Failure"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by kpmaddenuk on 2013-11-09
Hi,

I followed the instructions to setup a software RAID manually with the "alternate" install disk.
I have two WD 2Tb drives both with an 8Gb partition and another partition that takes up the rest of each drive.
I've then created a RAID1 giving me:
[INDENT]RAID1 Device #126 8.0 GB Linux Software RAID Array
#1              8.0GB  F  swap     swap
RAID1 Device #126 2.0 TB Linux Software RAID Array
#1              2.0TB  F  ext4   [/INDENT] 

The installation has then continued and all seems to be well. However, after the eject of the CD-ROM the attempt to boot from the HDD gives "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".

Anyone got any ideas what I need to do or haven't done?

Cheers - SD

---

### Post by kpmaddenuk on 2013-11-13
Ok, I found the problem.

It looks as though the HW RAID on the BIOS interferes with the SW RAID.

I disabled the SATA RAID in the Intergrated Periphals on my board (Award BIOS) and I could boot without problem.

---

