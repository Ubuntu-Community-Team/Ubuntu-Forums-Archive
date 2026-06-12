---
title: "Installation problem 10.04 USB LTS: Partition #1 Failed Raid"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by arachn1d on 2010-07-16
The ext4 file system creation in partition #1 of Serial ATA RAID isw_fjidifbhi_Volume0 (mirror) failed.

----

Not sure what's wrong? How do I solve this?


This happens after I enter my login details and click next. Then it fails on the install screen with this error. :(

---

### Post by arachn1d on 2010-07-16
I used GParted and wiped disc and now I get this

The ext4 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

---

### Post by ronparent on 2010-07-16
Typical of my experience with 10/04, gparted doesn't work on a raid. Thus, the partitioning step of the installation will fail! Workaround - Use an earlier version of ubuntu (installed or live cd to create and format any raid partitions you will need for the install. Select but do not format these partitions during the install. After that the install should proceed flawlessly except for possibly a fatal failure if you try to place the grub bootloader on the raid. That actually can be fixed. Post if you need more help.

Note: the problem doesn't appear to be with gparted, but with how gparted functions under 10.04. The same version of gparted is used under 10.04 as distributed with earlier versions of Ubuntu. A change in behavior under 10.04 doesn't let gparted see or work on raid drives or partitions.

---

