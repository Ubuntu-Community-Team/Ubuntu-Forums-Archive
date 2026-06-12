---
title: "Cannot install Ubuntu -"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by dserbia on 2010-05-06
Hello everyone,

I had 5 partitions on my computer with diffrent versions of Windows installed. Windows had trouble with network and viruses, so I decided to install Ubuntu.

I booted into the live CD, and selected to install Ubuntu to the whole hard disk (remove everything). It first formatted the disk, then it showed an error message.
Error message: The ext4 file system creation in partition #1 of Serial ATA RAID pdc_jcehbfgi (stripe) failed.

Now the hard disk is empty -> no system. Ubuntu won't install. I'm writing from the live CD. Can anybody help me?

---

### Post by dserbia on 2010-05-06
...no help?

---

### Post by lisati on 2010-05-06
Patience please! We are all volunteers here!

The usual guideline is not to bump posts more often than once a day.

---

### Post by Sef on 2010-05-06
1) From the Live CD, Applications > Accessories > Terminal

then copy and paste ins this code:

```
sudo fdisk -l
```

then copy and paste the results here.

That code will show what your paritions are.

2) How does it run with the Live CD?

---

### Post by dserbia on 2010-05-06
Fdisk:
```
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e580d

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2230

   Device Boot      Start         End      Blocks   Id  System

```The live CD runs well, a little slow (expected, it is a CD after all). I have no problems except I can't install.

**Edit**: I found [this]("http://ubuntuforums.org/showthread.php?p=9237640") and it seems to be the problem. However, I can't solve it. If anybody can provide help on how to do what was suggested in the thread it *may* be the solution :)

---

### Post by hayeksghost on 2010-05-06
I'm having the same problem as well.

---

### Post by dserbia on 2010-05-10
Bump...

---

