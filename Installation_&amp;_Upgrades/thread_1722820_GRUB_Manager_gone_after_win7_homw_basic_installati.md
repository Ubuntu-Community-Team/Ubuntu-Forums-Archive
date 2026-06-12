---
title: "GRUB Manager gone after win7 homw basic installation"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by telovin on 2011-04-06
Hello All,
I lost my grub manager after reinstallation of win 7 home basic. Wanna see grub there. My system when switched, firectly boots into win 7. Doesnt give me the boot menu.:confused:
So am unable to logon to my ubuntu.
Kindly help!

---

### Post by telovin on 2011-04-06
Hi,
Before going through recoveringubuntuafterwin7installation documentation, want to make sure if my ubuntu is there on my system.
I am attaching a screen shot of compmgmt screen,I cant see ubuntu there. Does that mean that win 7 installation wiped out my ubuntu n data with it?????????

---

### Post by Joe of loath on 2011-04-06
I assume that your Ubuntu installation will be the second partition in. It's not labelled because Windows can't read it.

---

### Post by coffeecat on 2011-04-06
**If** your Ubuntu partition is still there **and if** you did not install using Wubi, then this guide will help you reinstall grub using the live CD:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you need help interpreting the output of 'sudo fdisk -l' then post the output and we'll help you.

However, if there's any doubt about the first two ifs, then I suggest you run the boot info script which is always helpful with booting problems. Boot up with the live Ubuntu CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions on that page. Then post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags as described there. You can use the # icon on the message toolbar for this. With that output we will be able to see exactly what is on your machine and what needs to be done.

---

### Post by telovin on 2011-04-06
Hi,
I followed the grub reinstallation link and the results I got are as follows. It showed errors.

[PHP]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea6eea6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19456   115322602+   f  W95 Ext'd (LBA)
/dev/sda5            5100       10198    40957686   83  Linux
/dev/sda6           10199       15297    40957686    7  HPFS/NTFS
/dev/sda7           15298       19456    33407136    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo grub-setup -d /media/85a28086-45e8-476e-bd17-09e46e5ce2d5/boot/grub /dev/sda1
grub-setup: error: Cannot open `/boot/grub/device.map'
ubuntu@ubuntu:~$ sudo grub-setup -d /media/85a28086-45e8-476e-bd17-09e46e5ce2d5/boot/grub -m /media/85a28086-45e8-476e-bd17-09e46e5ce2d5/boot/grub/device.map /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: If you really want blocklists, use --force.[/PHP]

I tried  the following command after mounting ubuntu partition

 [PHP]sudo grub-install --root-directory=/mnt /dev/sda[/PHP]it did not show any errors. Let me reboot and see if it works.

---

### Post by telovin on 2011-04-06
Hi Coffee cat and Joe of loath,

The thread 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) is very useful.
I tried  the simplest method in the thread. After mounting my ubuntu partition,copied GRUB2 files from live CD  
I am writing this from my harddisk ubuntu. My grub is showing ubuntu and windows 7 :D.
The grub version is shown as 1.76 or something.May be I'll try updating it now and see if any latest version is available or not.

Thanks a lot Coffeecat and Joe of loath!:D

---

