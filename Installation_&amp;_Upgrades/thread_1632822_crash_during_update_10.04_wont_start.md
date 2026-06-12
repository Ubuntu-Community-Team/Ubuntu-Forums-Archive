---
title: "crash during update 10.04 wont start"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by mxman81 on 2010-11-28
hey
During update my pc locked up and i shut it down. power button :( now ubuntu wont start up, it runs straight to busybox, windows starts and runs normaly. 

i have tried to do some simple fix with a live cd (ubuntu 10.10, the instaled verison is 10.04) but everything stops after a while in the terminal. have tried to install grub + update and upgrad with terminal live cd. have also tried to run the [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) but stops when it comes to the partiotn thats ubuntu is on (sda5)disk

have also tried to install 10.10 from the cd, just starts to loading after chosen install...nothing happens.

anything i can do in busybox ? must i format the whole disk, including windows ?

---

### Post by mxman81 on 2010-11-29
sudo fdisk -l 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4e9d1542

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       19317   155057668    7  HPFS/NTFS
/dev/sda3           19318       38913   157404870    5  Extended
/dev/sda5           19318       38112   150970806   83  Linux
/dev/sda6           38113       38913     6434001   82  Linux swap / Solaris

---

### Post by mxman81 on 2010-11-29
Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg.


this is coming befor busybox starts.

---

