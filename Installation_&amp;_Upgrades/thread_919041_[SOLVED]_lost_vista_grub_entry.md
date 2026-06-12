---
title: "[SOLVED] lost vista grub entry"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by dirty_ol_rza on 2008-09-13
I had Vista/Ubuntu dual boot working but after Ubuntu wireless issues I re-installed Ubuntu and have lost my grub menu and go straight into Ubuntu.

I don't have Vista in my menu.lst just Ubuntu.
I was hoping someone could recommend what to add in.

Here's my fdisk -l    

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           11948       11978      249007+  82  Linux swap / Solaris
/dev/sda2           11979       14410    19535040   83  Linux
/dev/sda3   *           1       11947    95964246    7  HPFS/NTFS

Partition table entries are not in disk order

---

### Post by caljohnsmith on 2008-09-13
Try adding:
```
title Windows Vista
root (hd0,2)
makeactive
chainloader +1
```
If it seems like you've lost your Grub menu on start up, find the line near the beginning in your menu.lst that has "hiddenmenu" and instead put a # in front of it:
```
#hiddenmenu
```

---

### Post by dirty_ol_rza on 2008-09-13
Thanks for that!

It worked perfectly. yet again the forum has come to the rescue.


Many thanks

---

### Post by caljohnsmith on 2008-09-13
You're welcome; I'm glad you can boot all your OSes now. :) If it's not too much trouble, please click the "thread tools" link near the top of this thread and choose the "marked as solved".

---

