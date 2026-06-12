---
title: "Vista&amp;Ubuntu Dual boot"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by Ruy on 2007-03-06
I have install Ubuntu first then Windows Vista.
Windows Vista as replace the Grub Loader, but with the help of the Grub Boot Disk (ISO File) i can boot my computer via GRUB, and i want to configure them 

Here my definitions

[I]
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/hda2            5223        6527    10482412+  83  Linux
/dev/hda3            6528        6658     1052257+  82  Linux swap / Solaris
/dev/hda4            6659        7296     5124735   82  Linux swap / Solaris[/I]

i tried to configure grub to boot windows vista also:
t[I]itle           Windows Vista Ultimate
rootnoverify		(hd0,0)
makeactive
chainloader+1[/I]

when i restarted i cannot boot windows Vista.

Can you tell me why?

Thanks

---

### Post by st1905 on 2007-03-06
Try like this rootnoverify (hd0,1)

---

### Post by Ruy on 2007-03-06
the same thing.....

doesnt work :(

---

### Post by Ruy on 2007-03-07
I need help

---

### Post by dstew on 2007-03-07
The following are needed. I see two errors in your menu item:

rootnoverify (hd0,0)
chainloader +1
makeactive
boot

One, you need a space between chainloader and +1.
Two, you need the boot command.

---

