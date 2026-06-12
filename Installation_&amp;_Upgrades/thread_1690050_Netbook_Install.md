---
title: "Netbook Install"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by Firedude88 on 2011-02-17
I am attempting to install ubuntu netbook onto my recently purchased Asus Eee PC 1015PEM and where it should show three options for Allocate Drive Space, it only has two.  The option to install alongside another operating system is not there.  Since I wish to keep my Windows 7 partition I thought I could just make another partition using the Specify partitions manually option but I am unsure what to do in this advanced menu.  I don't want to accidentally clear any important partition.  If anyone could help me either with how to get back the "Install alongside another operating system" option or further explain how to manually edit the partitions that would be fantastic and I thank you now in advance for taking the time to help me.

---

### Post by mikewhatever on 2011-02-17
Can you post the output of **sudo fdisk -l** to give us an idea of the initial partition layout. The option you want back will only work on disks with one or two primary partitions, if you have three, then manual partitioning is in order, and if four, then you'll have to go with wubi or delete one of the partitions.

---

### Post by Firedude88 on 2011-02-17
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29133921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13055   104857600    7  HPFS/NTFS
/dev/sda2           13055       15013    15728640   1b  Hidden W95 FAT32
/dev/sda3           15013       30399   123590656    7  HPFS/NTFS
/dev/sda4           30399       30402       20664   ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 8005 MB, 8005787648 bytes
247 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      210485      226594   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(210484, 238, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(226593, 24, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       28267       78919   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(28266, 90, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(78918, 75, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      122082      247408   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(122081, 227, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(247407, 29, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      142148      142691     4161652    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(142147, 74, 31)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(142690, 200, 20)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by mikewhatever on 2011-02-17
Well, as expected, 4 primary partitions already in place, which means you can't create more without removing one. What are the two large ntfs partitions, /dev/sda1 and /dev/sda3?
PS: the second hdd loook a bit wacky.

---

### Post by Firedude88 on 2011-02-17
Thats just it.  I dont know.  I just got this netbook.  It is brand new out of the box.  I have no idea why there are four partitions already.  I dont know what is with the second partition that is fat 32. All I know is that it has one 250gb hardrive and that should be it.  maybe a recovery partition. thats all i can think of.

---

### Post by Firedude88 on 2011-02-17
I reloaded into windows and discovered that there now appears to be two partitions.  the normal local disk C  with windows installed. and there is now a second local disk D that was not there before.  It seemingly has nothing in it.  C has 99.9GB total and D has 117GB total. I am not sure how it happened but D seems to be a new blank partition that i never actually created.

---

### Post by mikewhatever on 2011-02-17
Sda2 could be the recovery partition, and sda3 appears to be for data, and if it's empty, you could use its space to install Ubuntu. What's sda4 is a mystery.

---

### Post by Firedude88 on 2011-02-17
ok i will try that.  One more question.  Do I need to format the partition a particular way for ubuntu?  If i recall right ubuntu uses a different filling system than ntfs.  Which one do I use?

---

### Post by mikewhatever on 2011-02-17
Yes, more like delete it and create partitions for Ubuntu, root and swap, both logical.

---

### Post by Firedude88 on 2011-02-17
thank you very much for your help.

---

### Post by Firedude88 on 2011-02-18
thank you very much for your help.

---

