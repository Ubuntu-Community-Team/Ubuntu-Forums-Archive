---
title: "Vista/Ubuntu Dual Boot"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by aguba on 2007-05-12
I installed Ubuntu but can't seem to get the GRUB loader. When I restart my comp, it goes straight to Vista. Any help, please?

---

### Post by aguba on 2007-05-12
bump please help

---

### Post by confused57 on 2007-05-12
> **aguba said:**
> I installed Ubuntu but can't seem to get the GRUB loader. When I restart my comp, it goes straight to Vista. Any help, please?
Boot up the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

---

### Post by aguba on 2007-05-12
Disk /dev/sda: 80.0 GB, 80000000000 bytes 
255 heads, 63 sectors/track, 9726 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           4       32098+  de  Dell Utility 
/dev/sda2   *           5        6689    53697262+   7  HPFS/NTFS 
/dev/sda3            6691        9119    19510942+   7  HPFS/NTFS 
/dev/sda4            9120        9725     4867695   db  CP/M / CTOS / ... 
 
Disk /dev/sdb: 80.0 GB, 80000000000 bytes 
255 heads, 63 sectors/track, 9726 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1               1           4       32098+  de  Dell Utility 
/dev/sdb2   *           5        5552    44558062+   7  HPFS/NTFS 
/dev/sdb3            5552        9119    28656240    f  W95 Ext'd (LBA) 
/dev/sdb4            9120        9725     4867695   db  CP/M / CTOS / ... 
/dev/sdb5            5552        7011    11718750   83  Linux 
/dev/sdb6            7012        7095      674698+  82  Linux swap / Solaris 
/dev/sdb7            7096        9119    16257748+  83  Linux 
 
Disk /dev/sdc: 32 MB, 32112128 bytes 
4 heads, 32 sectors/track, 489 cylinders 
Units = cylinders of 128 * 512 = 65536 bytes 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1         489       31270+   4  FAT

---

### Post by confused57 on 2007-05-12
You'll need to mount your Ubuntu partition & gather more information, then maybe we can determine what's going on...boot up the live cd, open a terminal, enter:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb5 /media/ubuntu
```
this will mount your Ubuntu partition & post the output of the following:
```
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```

I suppose sdc is a pen drive & you had it inserted when you install Ubuntu...if you Dell is like mine you can only boot first to the primary drive, in other words, you're not able to select booting first to the other hard drive in bios.

Post your menu.lst & device.map, "maybe" this will tell us something.  Copy & paste the above in a terminal one line at a time, pressing enter after each line.
Note:  menu.lst is short for menu.list

---

### Post by aguba on 2007-05-12
After mounting my partition, I got this:

wrong fs type, bad option, bad superblock on /dev/sdb5, 
       missing codepage or other error 
       In some cases useful info is found in syslog - try 
       dmesg | tail  or so

---

### Post by confused57 on 2007-05-12
Your better choice might be to try to boot Linux with the Vista bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

To install grub to the root partition, you can use the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
which would be something like this:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hdx,y)", then you would enter:
```
root (hdx,y)
setup (hdx,y)
quit
```

With your setup and hard drives, it might be much easier to boot Linux from EBCD.

---

### Post by aguba on 2007-05-12
Thanks for your help. I'll see if I can get this working using EBCD.

---

