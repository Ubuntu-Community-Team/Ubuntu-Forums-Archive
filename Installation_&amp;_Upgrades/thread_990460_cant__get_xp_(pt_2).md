---
title: "cant  get xp (pt 2)"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by ryan! on 2008-11-22
if u didn't know my computer goes straight to ubuntu without asking me if i want to go to xp and i would like it to ask me..... 
heres what i did
gksudo gedit /boot/grub/menu.1st .........# hiddenmenu ....... <sudo fdisk -1>         then i got

ryan@ryan-desktop:~$ sudo fdisk -1 
fdisk: invalid option -- '1' 
 
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors

when i restarted it didn't ask me which one i wanted .......help

---

### Post by lisati on 2008-11-22
Take a deep breath, all is not lost.
The option on the fdisk command should be a little "ell", not a number one:
```
sudo fdisk -l
```
and the file is menu.lst (again with a little "ell", not a number one:
> menu.lst

---

### Post by ryan! on 2008-11-22
thx for the quick reply and it looked like a 1 on my computer :lolflag::mad:

---

### Post by ryan! on 2008-11-22
ryan@ryan-desktop:~$ sudo fdisk -l 
 
Disk /dev/sda: 80.0 GB, 80000000000 bytes 
255 heads, 63 sectors/track, 9726 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xe686f016 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1         423     3397716   83  Linux 
/dev/sda2             424        9726    74726347+   5  Extended 
/dev/sda5            9375        9726     2827408+  82  Linux swap / Solaris 
/dev/sda6             424        9022    69071404+  83  Linux 
/dev/sda7            9023        9374     2827408+  82  Linux swap / Solaris 
 
Partition table entries are not in disk order 
ok so this is what i got..........now what

---

### Post by Sef on 2008-11-22
You overwrote Windows XP.  It is not there.   You might be able to recover it with [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  Hopefully you back up any data you needed that was on the XP partition.

---

