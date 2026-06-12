---
title: "machine goes directly into XP after installing ubuntu"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by GadgetsGuy on 2008-04-06
I just completed installing ubuntustudio onto a PC that already is running XP.

All seemed to go well, but upon rebooting the system, there is no GRUB bootloader, and no option to boot intu Ubuntu ... my computer just boots into XP as it always did.

My drive has been partitioned, and I do believe that ubuntu installed fully on the new partition, but it cannt be seen from XP of course ... 

So alas ... I am missing 30GB from my hard drive (the ubuntu partition), and I have no way to boot into Ubuntu.

Any help would be appreciated.

GG

---

### Post by Pumalite on 2008-04-06
Boot your Live CD and post>
sudo fdisk -lu

---

### Post by GadgetsGuy on 2008-04-06
I installed from the alternate CD ... it was not a live CD :(

---

### Post by Pumalite on 2008-04-06
Try to boot Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
I will need the output of a few commands.

---

### Post by GadgetsGuy on 2008-04-06
I found a ubuntu 6.06 Live CD ... and have booted into it ... however each time I go to open firefox, the monitor goes black and seems to lose signal, and the only way to rectify it is to reboot :(

---

### Post by GadgetsGuy on 2008-04-06
matter of fact the entire machine freezes up 20 seconds or less after booting into ubuntu

I am typing from my Windows laptop

---

### Post by sandysandy on 2008-04-06
any live cd will do for posting the command outputs

damm small linux, puppy linux etc

regards

---

### Post by GadgetsGuy on 2008-04-06
i boot the live CD and less than 20 seconds later my entire system freezes up ... 4 times now :(

brand new 3.2 Ghz core duo p4 with 1GB of ram

---

### Post by GadgetsGuy on 2008-04-06
OK .... Safe Graphics mode seems to have worked ... I am posting this from the machine running LiveCD ... albeit I cannot get the "florescent light effect" to go away, as it will not give me the proper refresh rate in the screen resolutions.

What output do I need to post?

---

### Post by GadgetsGuy on 2008-04-06
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   117210239    58605088+   7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    58605119    29302528+   c  W95 FAT32 (LBA)
/dev/sdc2        58605120   490223474   215809177+   f  W95 Ext'd (LBA)
/dev/sdc5       159991398   322906499    81457551    7  HPFS/NTFS
/dev/sdc6       322906563   490223474    83658456    b  W95 FAT32
/dev/sdc7        58605246   155750174    48572464+  83  Linux
/dev/sdc8       155750238   159991334     2120548+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             248     3932159     1965956    6  FAT16
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-04-06
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Get Super Grub and see if you can boot Ubuntu: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by GadgetsGuy on 2008-04-06
went step-by-step thru reinstalling grub .... and now when I reboot I get GRUB loading, please wait ... 
Error 21 

and that's all she wrote ....

I love ubuntu ... but it should not be this friggin hard to install!!!!!!!!

---

### Post by Pumalite on 2008-04-06
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by GadgetsGuy on 2008-04-06
OK .... now I'm kinda ****** ... as I cannot get the computer to boot into GRUB or windows ..

all I can do is let it load to Error 21 ... and then reboot - rinse and repeat  :confused:

---

### Post by GadgetsGuy on 2008-04-06
now to add insult to injury ,,,, XP recovery console is telling me invalid administrator password and booting me out ... WTF???????????????????

:confused:

---

### Post by GadgetsGuy on 2008-04-06
Ok Now How Do I Get Rid Of Grub????

Its preventing Me From Resetting My Xp Admin Password !!!

---

