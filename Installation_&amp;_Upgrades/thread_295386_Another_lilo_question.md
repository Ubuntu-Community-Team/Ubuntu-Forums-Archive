---
title: "Another lilo question"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by johnhcl on 2006-11-08
Hi, Newbie convert to Linux/ubuntu

I tried and failed to get dual lilo booting to work.

I have two ide disks, master = ubuntu, slave=xp

Can someone write the lilo.conf for me with the following details please?

It would be much appreciated. Thanks

root@john-desktop:~# /sbin/fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19175   154023156   83  Linux
/dev/hda2           19176       19457     2265165    5  Extended
/dev/hda5           19176       19457     2265133+  82  Linux swap /
Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9963    80027766    7  HPFS/NTFS
root@john-desktop:~# 


oot@john-desktop:/boot# ls -ltr
total 8876
-rw-r--r-- 1 root root   74645 2006-10-14 00:13 config-2.6.17-10-generic
-rw-r--r-- 1 root root 1636681 2006-10-14 03:09 vmlinuz-2.6.17-10-generic
-rw-r--r-- 1 root root  285604 2006-10-14 03:09 abi-2.6.17-10-generic
-rw-r--r-- 1 root root  728690 2006-10-14 03:09 System.map-2.6.17-10-generic
-rw-r--r-- 1 root root   94600 2006-10-20 19:44 memtest86+.bin
-rw-r--r-- 1 root root 5697530 2006-11-05 03:53 initrd.img-2.6.17-10-generic

---

### Post by .t. on 2006-11-08
I only used lilo in my "old" Linux days, before I used GRUB. Now I use GRUB, I have pretty much forgotten about lilo, so I won't be of too much help... May I ask why you are using lilo and not GRUB?

---

### Post by johnhcl on 2006-11-08
because I don't know any better.

If Grub is the way to go, I'll use it.

Is it similar to lilo, do you have to setup a config file?

---

### Post by Najand on 2006-11-08
Hmm, it has all the things a good boot manager needs to have. It has a config file which would be available under /boot/grub, but also configuration is possible through the "grub" command.

---

### Post by .t. on 2006-11-08
How did you get to be using lilo? The default for Ubuntu is GRUB?

---

