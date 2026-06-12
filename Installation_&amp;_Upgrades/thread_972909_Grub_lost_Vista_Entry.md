---
title: "Grub lost Vista Entry"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-11-06
Alright i know that this a simple question but i have been unable to fix it,
fdisk -l got me this.
[INDENT]Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b8055

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40d3549b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdb2            5223        6527    10482412+  83  Linux
/dev/sdb3            6528       30515   192683610    5  Extended
/dev/sdb5            7019       30515   188739652+   b  W95 FAT32
/dev/sdb6            6528        7018     3943894+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4126 MB, 4126146560 bytes
16 heads, 32 sectors/track, 15740 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x9bea1c7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15740     4029424    b  W95 FAT32[/INDENT]

This is the entry on the menu.lst that is supposed to be vista.
[INDENT]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1[/INDENT]

Thanks.

---

### Post by caljohnsmith on 2008-11-06
How about trying all three of these entries, because most likely one of them will work:
```
title Windows Vista #1
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Windows Vista #2
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title Windows Vista #3
root       (hd0,0)
chainloader +1
```
If none of them work, let me know exactly what happens when you try each of them from the Grub menu, and we can work from there. Otherwise let me know how it goes.

---

