---
title: "Boot Harddisc crashed"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by cemax on 2008-03-15
Hi all,

I was running two hard discs with:

Hard disc no:1 (sda) boot: Vista Home
Hard disc no:2 (sdb): Vista Ultimate, Ubuntu 7.02 (Wubi Installation)

All systems were loaded by Windows boot loader on HD1 (sda)

After a great crash of HD1 (sda) i´ve installed a new Ubuntu 7.10 on HD1 (sda)

Unfortunately Grub didn´t recognize the other Ubuntu 7.02 and Vista Ultimate on HD2 (sdb).

How can i implement the other OS´s into Grub of Ubuntu 7.10 on HD1?

fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e15abb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60045   482311431   83  Linux
/dev/sda2           60046       60801     6072570    5  Extended
/dev/sda5           60046       60801     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4b88177

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30409   244258808+   7  HPFS/NTFS
/dev/sdb2           30409       50603   162205688    7  HPFS/NTFS
/dev/sdb3           50603       60801    81917952    7  HPFS/NTFS

Thx in advance.
Cem

---

### Post by dstew on 2008-03-15
From your fdisk output, there doesn't seem to be a linux partition on your /dev/sdb drive.

---

### Post by cemax on 2008-03-16
/dev/sdb3 is a Linux partition using NTFS

I´m able to mount sdb3 (with Ubuntu 7.10 on sda) and see the "wubi", "boot", "grub", "wubi-save" folder

---

### Post by cemax on 2008-03-18
Any help? Any further details needed?

---

### Post by dstew on 2008-03-18
Post the output of ```
cat /boot/grub/menu.lst
```

---

### Post by cemax on 2008-03-19
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5158a041-9d0a-470f-b691-32cea40d8108 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5158a041-9d0a-470f-b691-32cea40d8108 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Vista
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

Even if you don´t see any Linux partition on sdb3 there is one. The new Ubuntu 7.10 installation on sda is able to mount sdb3 called Linux. It contains these folders: Wubi, Boot, Grub and these files: home.virtual.disk mit ca. 20Gb, system.virtual.disk und swap.virtual.disk

---

### Post by cemax on 2008-03-20
ok. i´ve solved with mounting the wubi virtual files and saving all necessary files to my new ubuntu.

here the link:

[https://wiki.ubuntu.com/WubiGuide#head-07237d770829d13ec121542d199fc3b34320a877](https://wiki.ubuntu.com/WubiGuide#head-07237d770829d13ec121542d199fc3b34320a877)

---

