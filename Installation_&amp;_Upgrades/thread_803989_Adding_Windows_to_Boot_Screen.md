---
title: "Adding Windows to Boot Screen"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by cyberyoda0 on 2008-05-22
Hi everyone.  This is my first time here, so sorry if I sound like a total noob. But here it goes:

My problem is that Win2k Pro doesn't show up on my boot screen (GRUB if I'm not mistaken).  From reading some of these threads, I think the reason it is gone is because the Ubuntu 8.04 install removed a partition.  I don't quite understand why it removed Win2k from the boot screen too, but oh well.

So, here's my *guess* how to fix it.  Running:
```
sudo fdisk -l
```

got me:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88a888a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15170   121852993+   7  HPFS/NTFS
/dev/sda2           15171       30401   122343007+   f  W95 Ext'd (LBA)
/dev/sda5           15171       30401   122342976    7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e03d107

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         830     6666943+  82  Linux swap / Solaris
/dev/sdb2             831        2491    13341982+   f  W95 Ext'd (LBA)
/dev/sdb5             831        1660     6666943+   b  W95 FAT32
/dev/sdb6            1661        1758      787153+  82  Linux swap / Solaris
/dev/sdb7            1759        2491     5887791   83  Linux
```

I think I found a solution, but wanted to run it by you guys before I do anything.  To me, it looks like Windows is installed on /dev/sda1.  So if I go to the terminal in Ubuntu, and type GRUB, then manually edit /boot/grub/menu.lst with:

```
title	Windows 95/98/NT/2000
rootnoverify	(hd0,1)
makeactive
chainloader	+1
```

I wasn't 100% sure where my Win2k was located on, so the "(hd0,1)" was a guess, can someone verify?

Will this work, or do I need to run the Repair option from my Win2k Pro disk?


Thanks a ton for any help,
-Billy

---

### Post by Pumalite on 2008-05-22
It's more like (hd0,0)
What's going on with sdb? You have the boot flag on the /swap partition.

---

### Post by cyberyoda0 on 2008-05-22
I'm not really sure about that.. I used to have Ubuntu 6.06 Dapper and the dual boot worked fine.  I wanted to upgrade to a newer version, but was too lazy to go through every upgrade, so I just formatted and installed 8.04.  That might be why things are a little bit wonky.

Is that a big problem, or should I just leave it?

Thanks for the reply!

---

### Post by Pumalite on 2008-05-22
Let's see. Did you edit menu.lst? Are you able to dual boot?

---

### Post by cyberyoda0 on 2008-05-22
Awesome! Thanks, it worked like a charm.

---

### Post by Pumalite on 2008-05-22
You are welcome. Good luck.

---

