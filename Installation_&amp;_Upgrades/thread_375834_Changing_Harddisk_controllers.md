---
title: "Changing Harddisk controllers"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by scottrick49 on 2007-03-04
Hi,

I had windows XP and my ubuntu installation working perfectly on the same computer.  Then I started having trouble with both my harddrives failing at the same timey and I believe the problem is a bad IDE controller on my motherboard since switching to the other controller fixed the problem.  Now, however, ubuntu fails to boot properly.  It will sit on the loading screen with the progress bar (but never make any progress) for a while before dumping me to what looks like a stripped down version of the os (text mode only).  I'm guessing that there is some way to fix this without reinstallation (since windows handled it very well and works fine). 

Can anybody help a newbie out?

---

### Post by scottrick49 on 2007-03-04
bump for luck

---

### Post by confused57 on 2007-03-04
> **scottrick49 said:**
> Hi,

I had windows XP and my ubuntu installation working perfectly on the same computer.  Then I started having trouble with both my harddrives failing at the same timey and I believe the problem is a bad IDE controller on my motherboard since switching to the other controller fixed the problem.  Now, however, ubuntu fails to boot properly.  It will sit on the loading screen with the progress bar (but never make any progress) for a while before dumping me to what looks like a stripped down version of the os (text mode only).  I'm guessing that there is some way to fix this without reinstallation (since windows handled it very well and works fine). 

Can anybody help a newbie out?
You might want to boot up the live cd & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

You'll need to do some "tweaking" in your menu.lst, since you changed the controller the Ubuntu hard drive is connected to.

---

### Post by scottrick49 on 2007-03-11
Hey, 

I was finally able to get my computer set back up (i am in the middle of a move...) and boot to the live cd.  Here is the output of 'sudo fdisk -l'

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        8732    70139758+   7  HPFS/NTFS
/dev/hdc2            8733       10011    10273567+   f  W95 Ext'd (LBA)
/dev/hdc5            8733        9879     9213246   83  Linux
/dev/hdc6            9880       10011     1060258+  82  Linux swap / Solaris

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        9729    78148161    7  HPFS/NTFS

```

All help is VERY MUCH APPRECIATED!    :)

---

### Post by scottrick49 on 2007-03-12
bump for luck one last time; otherwise im just gonna reinstall

---

