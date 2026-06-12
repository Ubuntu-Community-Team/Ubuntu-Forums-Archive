---
title: "Mount and fstab question"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by holz on 2007-04-13
Hi all

This is a new installation. my usb external disk is mounted automatically, and shows on the desktop. I would like to prevent auto mounting since I want to mount it as read write via fstab. I have
/dev/sdb1 /media/mydocs/ -t ntfs -o nls=utf8,umask=0222
in fstab, yet it always mount to /media/MyDcs which is the windows disk label. How do I stop that from happening? My external usb also has two ext3 partitions which are gparted copies, do no want them to mount either.

TIA

-h-

---

### Post by aysiu on 2007-04-13
If you want read/write on NTFS, you'll have to [use NTFS-3G](http://ubuntuforums.org/showthread.php?t=217009). Otherwise, NTFS is strictly read-only.

---

### Post by holz on 2007-04-14
Yes, i have that installed,but it is not the answer to my question.

---

### Post by alshurooqi on 2007-04-23
Hi,
remove the** auto** from the fstab mounting line:)

---

