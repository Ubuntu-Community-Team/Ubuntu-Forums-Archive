---
title: "Problem with installation to multiple physical disks"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by dhopcroft on 2013-05-27
My PC fails to boot when I make an installation across two disks.

Ubuntu 64 bit desktop 12.10 (It's all I had on hand, as bootable USB stick. But I can make another if this is the problem)
Motherboard is an Asus P9X79Pro


I have a new PC, with an SSD and a HDD, I want to use the following scheme to partition the disks.


On SSD  (/dev/sdc)
/
/boot
/usr


On HDD (/dev/sda or sdb)
/home
/var
/svn
swap


The installation seems to go fine and no problems are noticed. However when I boot the installation, all I get is a flashing cursor top left of the screen.


I am thinking this is a problem with GRUB, But am lost as to what it could be.


BTW the installation works fine on either SSD only and HDD only, I only get the problem when I try and split the installation across two drives.

---

### Post by sudo san on 2013-05-27
In the installation, where did you install grub to? If it is the only operating system on the PC, then it should have been to /dev/sda, not /dev/sda1 or 2 ect.

Also, do you know if your PC came with EFI hardware? If so, that will be the problem. Here is a handy documentation page about installing Ubuntu in EFI mode: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by dhopcroft on 2013-05-28
Thanks, It didn't occur to me the BIOS could cause problems. This is my fist PC with a UEFI BIOS, and particularly with this odd hard disk layout.

I have the settings in the BIOS set to to "something like" described in the link you gave. I'll have another go at installing later today. If I get chance :(

Cheers.

---

### Post by dhopcroft on 2013-05-28
Thanks again. My system is now booting as I wanted it, the info on the linked page you gave was what I needed. Also I upgraded my distro to the latest (13.04) :)

---

### Post by sudo san on 2013-05-29
Your welcome, and I'm glad to hear you got it working. Don't forget to mark your thread as solved.  :)

---

