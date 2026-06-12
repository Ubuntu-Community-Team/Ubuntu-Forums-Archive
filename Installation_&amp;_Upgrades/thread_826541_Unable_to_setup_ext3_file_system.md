---
title: "Unable to setup ext3 file system"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by volmark on 2008-06-12
I’ve installed second HD that was for formatted as NTFS with Windows 2003 on it.
Then I’ve formatted it with $ mkfs –t ext3 /dev/sdb1. Then it was partitioned with sudo cfdisk. 
I could mount it and generally it works fine except when check this with sudo fdisk –l it still reports wrong file system: 

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9728 78140128+ 7 HPFS/NTFS

I have done it multiple times just to be sure that I done all the steps correctly but it still reports file system is HPFS/NTFS

Is there simple way to destroy NTFS partition tables and boot record on my second HD ?? Long time ago I’ve used low level utility for Windows where I could reset HD’s sectors manually bit by bit. Is there something similar for Linux ??

---

### Post by iaculallad on 2008-06-12
Try to use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") utility. The partition table might not have been updated.

---

### Post by volmark on 2008-06-12
I’m quite newbie in Linux environment that’s why I need further instructions. 
What TestDisk version should I download, for kernel 2.4 or 2.6 ??
How can I detect my kernel vers??
How I can install TestDisk from …tar.bz2 ??

---

### Post by iaculallad on 2008-06-12
> **volmark said:**
> I’m quite newbie in Linux environment that’s why I need further instructions. 
What TestDisk version should I download, for kernel 2.4 or 2.6 ??
How can I detect my kernel vers??
How I can install TestDisk from …tar.bz2 ??

You can detect your kernel version by entering the command (using terminal):

```
uname -a
```

Just download the [SystemRescueCd]("http://www.sysresccd.org/Main_Page"), it has a built-in TestDisk utility on it.

---

