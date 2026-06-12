---
title: "Grub Error 18"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by taz5005 on 2007-07-29
I am changing my computer from dual boot Win-XP and Gentoo to Win-XP and Ubuntu.  One of my hard drives (I'd have to assume it's the primary) is a 20 GB with Windows on it and the other is 120 GB that I'm planning on putting Ubuntu on (it used to have Gentoo).  

I installed Ubuntu and the reformatting and everything went fine, but when I started back up the computer Grub comes up with Error 18 and I can't do anything with it anymore.  I read up on what Error 18 is, and I'm pretty sure I understand the problem, but I don't know how to go about fixing it.  

I tried to "Setup" Grub from its command prompt into the first partition of the first hard drive.  I also tried to reinstall Grub:
sudo grub-install /dev/sd*
but with every one of those (most importantly sda), it says
"Could not find device for /boot: Not found or not a block device"

Could my problem be that the first partition is too big and I'm still writing too far into the disk?
If so, how would I go about fixing that?

If that isn't the problem, (or if there is a better way of fixing the problem), what could I do?

---

### Post by Pumalite on 2007-07-29
Try Super Grub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by taz5005 on 2007-07-29
I got SuperGrub and am trying things out with it, but I'm not getting anywhere.  When I try to Reinstall Grub manually or automatically from Super Grub Disk, it says it fails.  
I don't know if this would be any help, but fdisk -l gives me:

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1217     9775521    7  HPFS/NTFS
/dev/sda2            1218        2433     9767520    f  W95 Ext'd (LBA)
/dev/sda5            1218        2433     9767488+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14759   118551636   83  Linux
/dev/sdb2           14760       14946     1502077+   5  Extended
/dev/sdb5           14760       14946     1502046   82  Linux swap / Solaris

Any help would be huge!!

---

### Post by Pumalite on 2007-07-29
Try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Super Grub is better for your kind of problem though. You just have to follow the instructions carefully and to the letter.

According to your data Grub is installed to sdb1 and should be in MBR in sda1 (hd0,0). Assuming you installed XP first and Ubuntu second.

---

### Post by taz5005 on 2007-07-29
I'm pretty sure by default it installed Grub to sdb.  I've been trying to install Grub to sda, but when I try, this is what happens:
```
$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.


```

This same thing happens when I repeat the install command for any of my partitions.

I will go back and look again at Super Grub, see what I can do.

---

### Post by Pumalite on 2007-07-29
Re-install and when you get to step 7, go to 'Advanced Tab'; set bootloader to (hd0,0). Before you re-install, get Gparted:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Boot up and make sure you clean your partition and leave it setup for the installation. ( Make sure is made and available ).

---

### Post by MQMike on 2007-07-29
(To insert another option here that you may wish to try if all else fails. . .)

You need to re-install GRUB (to the Windows MBR, (hd0))
Since SGD didn’t do it, you can try it manually: 

Case 1:  You are able to boot into Ubuntu on your PC.
If so, do so.  Then open a terminal get a GRUB prompt as root by typing sudo grub  (then press Enter), and type the following (press Enter after each command):
grub>  root (hd1,0)          # (hd1,0) is the partition of your Ubuntu
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR
grub>  quit
$ exit

Case 2:  You can't boot into any of your Linux OSs.
First, you need to get a grub prompt (grub>) somehow.  Your two choices are: (1) Use a rescue disk, like Super Grub Disk, from which you can boot into your OS, or press the “c” key to get a GRUB prompt.  Or, (2) Use your Live Ubuntu CD.  Let's assume (2) here.  Put your Live CD in the CD tray, re-boot your PC, startup your Live Ubuntu.  Now get a terminal  and proceed exactly as in Case 1, starting with “sudo grub” to get a GRUB prompt.



How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

