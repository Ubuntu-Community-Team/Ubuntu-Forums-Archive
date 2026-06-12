---
title: "Triple Boot Problems with XP, Ubuntu, Fedora 7"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by godparticle on 2007-10-15
Having tried searching and various HOW-To's...no joy.  My original installation was 2 80G IDE Drives XP and Ubuntu, dual booting fine with grub.  Added a SATA drive, and tried to triple boot with new installation of Fedora 7.  Installed  Fed 7 with grub installed to /boot of SATA and then tried to chain load Fed 7, with

> 
title		Fedora 7.0
root		(hd2,0)
chainloader	+1



  Grub fails with error 13.

sudo fdisk -l

yields the following:
> 
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x204e295d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      208844      104391   83  Linux
/dev/sda2          208845   398283479   199037317+  8e  Linux LVM

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   160071659    80035798+   7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e27c93a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2   *          63    82140344    41070141    f  W95 Ext'd (LBA)
/dev/hdb3        82140408   160071659    38965626   83  Linux
/dev/hdb5        78734628    82140344     1702858+  82  Linux swap / Solaris
/dev/hdb6             189    78734564    39367188   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07065b64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   398283479   199141708+   7  HPFS/NTFS

any suggestions or is it time to bite the bullet and re-install all 3, not something I really want to do.:(

---

### Post by Pumalite on 2007-10-15
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

---

