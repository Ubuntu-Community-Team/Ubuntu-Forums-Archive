---
title: "Grub2 &amp; Xorg.conf"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by doktormiod on 2009-08-23
Hi, I installed Kubuntu 9.10 and everything works great except 2 things.
1. Grub didn't find my windows partition and i read that grub.cfg, unlike menu.lst, shouldn't be configured manually, so where and how can i add my windows partition to grub?

2. There is no xorg.conf file so how can i enable my fglrx drivers after installing them? Normally i just changed 1 line in that file (driver "ati" -> "fglrx")

PS. Just in case for the 1st question this is my fdisk -l:
```
isk /dev/sda: 160.0 GB, 160041885696 bytes
102 heads, 51 sectors/track, 60088 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25984    67584358+  83  Linux
/dev/sda2           25985       51601    66629817    f  W95 Ext'd (LBA)
/dev/sda5           25985       51601    66629791+   7  HPFS/NTFS
```

---

### Post by ranch hand on 2009-08-23
The first thing to do is try to run  sudo update-grub  again.  It was run when you installed and should have picked up your MS install.

---

