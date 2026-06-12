---
title: "GRUB booting issues/ xp wont work!"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by evering82 on 2008-05-22
Hi guys--I recently installed 8.04 and now I cant get windows xp to boot--can you offer any tips to a newb? 
When I attempt to boot into xp, I get "Error 12; invalid device requested"  


#this is sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x184c184b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       19928   160063627+   f  W95 Ext'd (LBA)
/dev/sda2           21458       24321    23005048+   7  HPFS/NTFS
/dev/sda5               2       19928   160057288+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10da10da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       35922   288543433+   7  HPFS/NTFS
/dev/sdb2           35923       38913    24025207+   5  Extended
/dev/sdb5           35923       38783    22980919+  83  Linux
/dev/sdb6           38784       38913     1044193+  82  Linux swap / Solaris

this is grub's menu.1st

default 0
timeout 10

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=cf643226-f43c-4d2f-bc82-1c7f3a927348 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=cf643226-f43c-4d2f-bc82-1c7f3a927348 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-12-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=cf643226-f43c-4d2f-bc82-1c7f3a927348 ro quiet splash
initrd /boot/initrd.img-2.6.24-12-generic

title Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-12-generic root=UUID=cf643226-f43c-4d2f-bc82-1c7f3a927348 ro single
initrd /boot/initrd.img-2.6.24-12-generic

title Ubuntu 8.04, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin

title Other operating systems:

title Windows Vista/Longhorn (loader)
root /dev/sdb1
chainloader +1
savedefault
makeactive

any help would be greatly appreciated--I just dont want to format and start from scratch with both oses again.  Thanks!

---

### Post by meierfra. on 2008-05-22
try

title Windows Vista/Longhorn (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1


There is some chance  that the  boot information is on /dev/sda2.
So if the above did not work, try


title Windows Vista/Longhorn (loader)
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

---

