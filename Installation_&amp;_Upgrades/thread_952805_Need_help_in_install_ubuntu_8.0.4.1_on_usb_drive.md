---
title: "Need help in install ubuntu 8.0.4.1 on usb drive"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2008-10-19
Hi,

I followed the following documentation to install ubuntu on usb drive:
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

I have 2 hard drives on my laptop:
1. hard drive internal to laptop (install windows), the primary partition
2. 2nd hard drive internal to laptop (install an old ubuntu), the slave partition
3. usb drive (which i just install ubuntu 8.0.4.1)

But the problem is i can't boot from the usb drive (I never get the boot selection screen from the usb ubuntu).  I have changed to bios to boot from usb drive before both internal hard drive. 

But the strange thing is this works:
1. I boot from my old ubuntu in my 2nd internal hard drive all the way to the login screen. (with my usb drive disconnect first and then connect it while the orange bar progress bar shows up).
2. without even log in, restart my laptop.
3. then my laptop can boot from the usb drive, shows me the new boot selection screen , and i can boot from the new ubuntu.

Can you please suggest what I can do so that i don't need to boot 2 times before i can boot from the new ubuntu? i would like to boot straight from my new ubuntu.

Thank you for any suggestion.

---

### Post by Pumalite on 2008-10-19
Read this thread:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by yinglcs2 on 2008-10-19
Thanks for pointing me to that thread.
But my situation is kind of different. 

I am using a usb drive (not usb thumb drive), like the WD passport drive.

I am able to boot from my usb drive after I boot from my old ubuntu from my internal hard drive once (all the way to the login screen), and then reboot my laptop.

So I don't understand how/what did booting the old ubuntu from my internal hard drive can do to the usb drive so that I can boot from usb drive?

Thank you for any more pointers.

---

### Post by Pumalite on 2008-10-19
Connect your USB Drive and post:
sudo fdisk -lu
(boot a Live CD if you have to)

---

### Post by yinglcs2 on 2008-10-19
Hi,

I login to the old ubuntu partition (installed on my internal hard drive), and connect to my usb drive with my new ubuntu installed.

I think:
/dev/sdc is my usb drive
and 
/dev/sdb is my internal drive with my old ubuntu installed.


```


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        61432560   185968439    62267940    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       185976000   195365519     4694760   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5       155252223   155461004      104391   83  Linux
/dev/sda6       155461068   185968439    15253686   83  Linux
/dev/sda7        61432686    90783314    14675314+  83  Linux
/dev/sda8        90783378    95667074     2441848+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44e4be6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     4883759     2441848+  82  Linux swap / Solaris
/dev/sdb2         4883760    64468844    29792542+  83  Linux
/dev/sdb3        64468845   117210239    26370697+  83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    58653314    29326626   83  Linux
/dev/sdc2        58653315    62557109     1951897+  82  Linux swap / Solaris
/dev/sdc3        62557110    80839079     9140985   83  Linux
/dev/sdc4        80839080   144327959    31744440   83  Linux


```

Thank you for any help.

---

