---
title: "Trying to install feisty on nv raid 0...need help"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by so_simple on 2007-03-30
I'm trying to install feisty beta on my pc and i have a nforce680i with 2 HD in raid0. 
When i install feisty, he dont detect my filesystems. i already have 4 filesystems (2ntfs, 1ext3, 1swap) because i install fedora core 6 and he detected the filesystems. 

Now i want to install ubuntu and i dont know how!

Can you help me?!?

---

### Post by DJMatty on 2007-03-30
I have spent a lot of time to try to get this working on my 680i mobo, in the end, after reading and attempting many of the how tos and posts about this i did the following:

1) Installed ubuntu onto my SATA drive (non-raid)
2) Boot into the installed version
3) Installed dmraid (sudo apt-get install dmraid)
4) Booted back into the live cd
5) Installed dmraid
6) Mounted the raid partitions
7) Mounted the sata partitions
8 ) Copied the sata install onto the raid drives
9) Modified fstab to have my raid partitions mounted instead of sata drive
10) Modified menu.lst to have the correct settings for the new partitions
11 Installed GRUB onto the boot partition of the raid drive
12) Set up my boot manager to boot the raid partition

Rebooted and it picked up and booted into Ubuntu on my raid drives. I have written the steps from memory, and I am not sure if there were other things that needed to be done to move the install from one drive to another, but there are how-tos about doing this.

This then worked great for me for about a week, until I installed updates a few days ago and now none of the kernels will boot anymore... :confused:  I don't know if this is due to raid, my 8800gtx gfx card or what, as I can't seem to find out what is causing the boot to fail, so it's back to the drawing board for me. Might just give up and install it all again on SATA drive and leave it there as it's easier to rebuild :)

HTH

Matt

---

### Post by DJMatty on 2007-03-30
Ooh also between items 3 and 4 I also changed the initramfs-tools udev file and added 'udevsettle timeout=10' to the bottom of it so that it gives dmraid a chance to detect the raid partitions when it's booting, otherwise the boot fails.

I don't have the exact bug report/posts to hand atm, but i am sure a little googling will return the info you will need... let me know if you have problems and I can dig out the specific pages for you.

Matt

---

### Post by so_simple on 2007-03-30
the problem is that i have 2 ntfs and one have 200gb of information that i dont want lose!

---

### Post by DJMatty on 2007-03-30
Yeah, I'm not sure what else you can do, as that was the only way I could get Ubuntu installed on my raid drives on my setup. None of the how-to's that I tried would work.

Could you just plug an additional HD in for the duration of the install, install to that, then copy the installation to the partitions on the raid drive?

Matt

---

