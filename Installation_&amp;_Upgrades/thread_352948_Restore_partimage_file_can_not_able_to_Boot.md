---
title: "Restore partimage file can not able to Boot"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2007-02-04
I want to restore partimage image to backup Harddisk, After restored just shown 
"No operating System". Checked the partition is OK.

Below is RescueCD fdisk list.

All the partition created base on my primary hard disk. The Backup hardisk just for other Linux installation. Now, back to Ubuntu. 


How to fix this problem ?

The number of cylinders for this disk is set to 2501.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2414    19390423+  83  Linux
/dev/hda2            2415        2495      650632+   5  Extended
/dev/hda5            2415        2495      650601   82  Linux swap / Solaris

Command (m for help):

---

### Post by moonhk on 2007-02-04
I fixed the problem. Just run install CD in rescue mode, Reinstall GRUB loader.
The Boot Loader can be able to Boot the /dev/hda1 boot section.

---

