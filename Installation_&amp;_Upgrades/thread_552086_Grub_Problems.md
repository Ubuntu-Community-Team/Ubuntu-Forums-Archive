---
title: "Grub Problems"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by Arukas on 2007-09-16
Hello, 

  I have a slight issue with my boot Grub.  It currently doesn't exist.  I have read on the forums, and so far, I haven't come across anything that has fixed the problem at all.

  I have windows install on my hard drive, and trying to dual boot them.  I have a Ubuntu LiveCD and only one harddrive.  

I have tried the commands to install the boot grub:


sudo grub
find /boot/grub/stage1
Error 15: File not found


There is no grub folder in my boot directly, I looked.  I don't have any other harddrives either.  My grub don't exsist and I can't make it appear, anyone know how to fix this problem?


-Arukas

---

### Post by Mr Gary on 2007-09-16
You will re-install the Grub with do the followings:

1)Boot from Ubuntu Live cd
2)When it olad the grafikal interface open a terminal
3)Sudo Grub
and then type root [hd0,x] or whatever belongs to your harddisk/partition you have installed Ubuntu and Quit.

I hope You made it...

---

### Post by confused57 on 2007-09-16
Boot the Ubuntu live cd, open a terminal and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

I assume you're not getting the grub boot menu, but your system is booting into Windows OK?  Did you get any errors during the grub install step when you installed Ubuntu?

---

### Post by Arukas on 2007-09-16
Hello again:

  When I boot up my computer, i get "Error loading Operating system"  So nothing boots up.  Also, using the terminal to reinstall grub does not work.  I've tried several times.


-Arukas




Here is the output from sudo fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19699   158232186    7  HPFS/NTFS
/dev/sda2   *       19700       38156   148255852+  83  Linux
/dev/sda3           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19929   160079661    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2007-09-16
Since confused57 doesn't seem to be logged in I'll try to help you:
You need to post your menu.lst now. Boot from Live CD, mount partition and in Terminal: cat /boot/grub/menu.lst
Post output here. We probably need to edit it.

[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Arukas on 2007-09-16
When I said the grub folder doesn't exist, I wasn't kidding.  I can't find a boot/grub folder anywhere, and neither can the termial commands.


-Arukas.

---

### Post by Pumalite on 2007-09-16
Did you mount the partition(your filesystem)?. If you read from Live CD itself, you will not find folder.

---

### Post by Arukas on 2007-09-16
I fixed the problem.   Apparently my LiveCD got damage somehow, (it installed fine on my laptop), so I made a new liveCD and it worked like a charm.   

Thank you all for you help.


-Arukas

---

### Post by Pumalite on 2007-09-16
You are welcome. Good luck.

---

