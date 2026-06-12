---
title: "XP install possibly corrupt after installing ubuntu"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by themusicalduck on 2008-12-02
Hey, I set up a dual-boot system with ubuntu and XP on one single drive, two partitions. Since installing ubuntu, I can't boot into Windows any more because NTLDR is missing. Using fixmbr, fixboot or bootcfg /rebuild doesn't help and if I try to use a windows boot disk, it says it can't find ntoskrnl.exe. chkdsk also can't scan the drive because of some major error and gparted can't scan it either. I can't mount or access any data on that drive from ubuntu.

This is the error from gparted after trying a disk scan:

```
GParted 0.3.8

Libparted 1.8.9

Check and repair filesystem (ntfs) on /dev/sdc1  00:00:00    ( ERROR )
     	
calibrate /dev/sdc1  00:00:00    ( SUCCESS )
     	
path: /dev/sdc1
start: 63
end: 123154289
size: 123154227 (58.72 GiB)
check filesystem on /dev/sdc1 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sdc1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sdc1' as NTFS failed: Invalid argument
The device '/dev/sdc1' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).

========================================

```

I can probably assume from all of this that my windows partition got corrupt at some point and can't be accessible either way.

Is there a way to recover this? Or is it just a case of reinstalling windows? and presumably if I want to use the same drive again, reinstalling ubuntu as well?

---

### Post by Pumalite on 2008-12-02
Search for 'meierfra' in this forum. He has a good XP repair thread.
[http://ubuntuforums.org/showthread.php?t=813628&highlight=meierfra](http://ubuntuforums.org/showthread.php?t=813628&highlight=meierfra)

---

### Post by themusicalduck on 2008-12-02
That looks like what it is I need to do, but since I can't mount or access any data on the partition, I can't replace the missing files.

---

### Post by Mark Phelps on 2008-12-02
Do a "sudo fdisk -lu" (that's a small "l", not a one) and post the results here.  That will at least confirm whether or not your Windows partition still exists.  If it does, you may be able to use testdisk to repair it.

---

### Post by Pumalite on 2008-12-02
You can also use Super Grub to boot/repair your XP:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

