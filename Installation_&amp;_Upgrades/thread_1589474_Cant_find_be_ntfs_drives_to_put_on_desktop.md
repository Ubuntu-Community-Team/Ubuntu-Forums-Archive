---
title: "Cant find be ntfs drives to put on desktop"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by unclebob1 on 2010-10-06
HI ... just started using Ubuntu 

running 
Release 10.04(lucid)
Kernal linux 2.6.32-25-generic
Gnome 2.30.2 

first installation of ubuntu before udating process because on lost audio sound due to drive issues ect ...all 2 hard drives were recognisable. want to put them on my desktop.

After upgarde that are not visable only if in type sudo fdisk -1


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45dc9d03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4d3d486

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19456   156280288+   7  HPFS/NTFS


tried using pmount but no joy !!! 

dont know how to find via something like on Xp control panel or my computer ?? 

suggestions please and remember i'm a new user so simplified  answers only ...still getting to grips with this.

---

### Post by unclebob1 on 2010-10-06
Sorted ...went into drive utility and mounted them !!!!!

---

### Post by Zimmer on 2010-10-07
Tip..
DO you have any Gnome type panels with Xubuntu (not used it myself)..?

Right click on one of your Gnome panels and Add to Panel , Disk Mounter. 
Handy applet for mounting/unmounting your partitions.

If no panels, then maybe you can install the applet in Xubuntu in some fashion...

EDIT: looking at the Xubuntu home page it appears you have the Gnome panels :)

---

