---
title: "grub loading error 15"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by maineman2 on 2008-02-17
Hi I have an ubuntu suse dual boot last night I added another partition now when I try and start the computer I get the message loading grub Error 15  and end up a prompt  Im pretty new to linux so try and keep the answers pretty descriptive Im now using the puppy linux live cd to get on the internet Thanks Dan

---

### Post by confused57 on 2008-02-17
> **maineman2 said:**
> Hi I have an ubuntu suse dual boot last night I added another partition now when I try and start the computer I get the message loading grub Error 15  and end up a prompt  Im pretty new to linux so try and keep the answers pretty descriptive Im now using the puppy linux live cd to get on the internet Thanks Dan
You might want to post the output of:
```
fdisk -l
```
-l is a small "L"

We need a little more info on where you added the new partition...did you resize either Ubuntu or Suse & create a new logical or primary partition?

If you're getting a grub boot menu, you could try highlighting your Ubuntu(or Suse) entry, press "e", highlight the root line, press "e" again, try changing root partition number...for example, if your root is (hd0,2), change it to (hd0,3), press "enter", then "b" to boot.  These changes are temporary, so it won't hurt your current setup, but may be worth trying.

You could also mount your Ubuntu &/or Suse partitions, & post your menu.lst:
```
nano /boot/grub/menu.lst
```
menu.lst is short for menu.list...I'm not sure which text editor is available in Puppy, but I think you will be prompted which text editor to use, if you use one that's not available.

---

### Post by Pumalite on 2008-02-17
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by maineman2 on 2008-02-17
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c3537

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         269     2104515    b  W95 FAT32
/dev/sda3   *         270         294      200812+  83  Linux
/dev/sda4             295        9729    75786637+   f  W95 Ext'd (LBA
/dev/sda5            3307        7358    32547690   83  Linux  ---------------ubuntu
/dev/sda6             456        1499     8385898+  83  Linux-------------------------------suse
/dev/sda7            1500        3066    12586896   83  Linux-------------------------------suse     Idont know why suse split upon installation
/dev/sda8             295         455     1293169+  82  Linux swap / S

Partition table entries are not in disk order
linux:~ #

I am now using the suse live cd to get on the internet. I shrank the ubuntu partition from 50 gib to 30 Thanks dan

---

### Post by confused57 on 2008-02-17
I'm not sure how your partitions are set up, for example it would help if you could describe your partitions:
```
/dev/sda1 1 7 56196 de Dell Utility
/dev/sda2 8 269 2104515 b W95 FAT32
/dev/sda3 * 270 294 200812+ 83 Linux <------Boot
/dev/sda4 295 9729 75786637+ f W95 Ext'd (LBA
/dev/sda5 3307 7358 32547690 83 Linux <------Ubuntu
/dev/sda6 456 1499 8385898+ 83 Linux  <-------Suse
/dev/sda7 1500 3066 12586896 83 Linux <-----New partition
/dev/sda8 295 455 1293169+ 82 Linux swap / S
```

I believe the simplest and easiest thing for you to try first is to install Ubuntu's grub(IPL) to the mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

This may work, especially if you installed Suse after Ubuntu.

---

### Post by maineman2 on 2008-02-17
I reinstalled suse and it all works fine Thanks Dan

---

