---
title: "grub error 22 - hardy"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by xigen on 2008-02-09
I get a grub 22 error when I boot up my new linux box

Amd 64 / hardy
500 gig sata drive 
200 gig ata drive

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000abf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60049   482343561   83  Linux
/dev/sda2           60050       60801     6040440    5  Extended
/dev/sda5           60050       60801     6040408+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1332

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       22351   179534376   83  Linux
/dev/hdb2   *       22352       24233    15117165   83  Linux
/dev/hdb3           24234       24321      706860    5  Extended
/dev/hdb5           24234       24321      706828+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> 

grub> 	
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: /boot/grub: No such file or directory
ubuntu@ubuntu:~$ 

How do you suggest I get grub to work and boot into the 500 gig SATA drive?

Thanks in advance.

---

### Post by gkestrel on 2008-02-09
The error 22 that you are getting means that grub cannot find the partition that you are telling it to boot from. First try manually editing the grub startup, when you see the grub screen press e to be able to get into edit mode, if you dont see the grub screen press escape then press e to edit the menu. Look for the line root   (hd0,0) this means grub is looking at the first hard disk and the first partition on it, if your ubuntu is on the second disk use the arrow keys to move the highlight to the right line press e to edit it and change it to root   (hd1,0) you can now press b to boot using the new temporary setting and see if this works you might have to do this more than once until you find the correct setting. If you get a successful boot then edit the menu.lst again to make the changes permanent.  Ubuntu sometimes gets confused when you mix sata and ata drives.

You could also try a copy of the super grub disk to attempt to fix grub but this might only last until the kernel is updated.  If this happens the device map is probably wrong try the following method that i have used on several ocassions.

If you get problems every time grub is updated with ubuntu failing to boot use this method.
To get update-grub working correctly, do the following:

before starting make sure to backup /boot/grub/menu.lst and /boot/grub/device.map
1. Fix your /boot/grub/device.map	type sudo gedit /boot/grub/device.map and change it mine was like below:
(hd0)	/dev/sda
(hd1)	/dev/sdb
i changed it to:
(hd0)	/dev/sdb
(hd1)	/dev/sda

2. rename /boot/grub/menu.lst 
3. Run update-grub	sudo update-grub

Note: when i did this it correctly updated menu.lst however it failed to add the other operating systems part.  To fix this i copied it from the old menu.lst and pasted it into the newly created menu.lst also if you have any splashscreen enabled you will need to add again the line

---

