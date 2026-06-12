---
title: "Gparted Doesn't See Hard Drive"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by varanasi on 2007-12-02
I am installing 7.10 on a sata drive to replace my gentoo installation.  The livecd boots and runs fine, but gparted finds no hard drive at all.  

When I do:
```
sudo fdisk -l
```
I simply get the ubuntu prompt.

fdisk -l in gentoo shows this:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131   83  Linux
/dev/sda2               6         193     1510110   82  Linux swap / Solaris
/dev/sda3             194        9729    76597920   83  Linux
```

The motherboard is a ps83-bc/bl w/intel 865pe.  

I am out of ideas and would appreciate your help.

---

### Post by Pumalite on 2007-12-02
User Gparted Live CD:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it. Make a large partition of your whole hard drive formatted ext3. Now install Ubuntu.

---

### Post by varanasi on 2007-12-03
Thanks for the suggestion.

I believe the problem was that my drive was connected to the motherboard as sata2, which means that it would be /dev/sdb instead of the typical /dev/sda.  When I switched the connector, the Ubuntu install cd noticed the drive.

---

### Post by Pumalite on 2007-12-03
Good luck!

---

