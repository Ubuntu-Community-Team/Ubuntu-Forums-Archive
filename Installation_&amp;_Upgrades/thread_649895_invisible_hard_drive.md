---
title: "invisible hard drive"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by univac on 2007-12-25
I'm trying to install Gutsy on my desktop. The problem is, when I want to prepare partitions, I can't see the disk I want to use. I have two other internal drives, both visible and partition-able. But the one I want to use doesn't show up. When I explore the computer from the Live CD, the same thing happens: the drive is nowhere to be found. I used Partition Magic to create ext3 and swap partitions in addition to the NTFS partition on the drive, and didn't have any problems. But Ubuntu doesn't see the drive. What am I doing wrong?

---

### Post by taurus on 2007-12-25
From the LiveCD, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by univac on 2007-12-26
> **taurus said:**
> From the LiveCD, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

OK. Here it is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee4fd345

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca28a85d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   42  SFS

---

### Post by univac on 2007-12-26
I should add that the drive I want to install Ubuntu on is not one of those listed. I can boot up fine into XP, which is installed on that drive.

---

### Post by univac on 2007-12-26
I figured it out. Here's the solution, for posterity: SATA cables were plugged into the motherboard randomly. Connected the drive in question to Port 0, and Ubuntu installation CD is now able to recognize it.

---

