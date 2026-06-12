---
title: "Doing a new fresh install Dual boot."
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by MCBTunes on 2008-01-10
I am not new to Ubuntu, however it has been awhile since I've done an install so I have a few questions

Are there any driver etc issues with Ubuntu 64 bit? I am dual booting with Vista 32 bit as vista64 sucks :), should I go with ubuntu 64 or 32? My machine will support the 64 bit.

I recall it works better installing windows first. So do I create a partition for vista, then use the remainder for Ubuntu, swap, or give vista it all and resize the partitions? How do I make sure I can access my windows files from hda1 on ubuntu like I do on my XP/Ubuntu machine (mounting I think it is called)?

What formats should they be? Should I make them both FAT(32) or NTFS?

Is there anything I need to know regarding the mbr?

Anything else?

---

### Post by zvacet on 2008-01-10
In case that you don´t have more than 4GB of ram I will go for 32 bit,because some things are easyer to install.if you want dual boot install Vista first.Read [this](http://ubuntuforums.org/showthread.php?t=371530&highlight=vista).Ubuntu use ext3 format.

---

### Post by MCBTunes on 2008-01-10
i have exactly 4gb. My hardware consists of

Asus M2N-Sli Deluxe
AMD Athlon64 X2 4000+
4GB ddr2 667Hz Memory
BFG 8800GT OC2 GPU

---

### Post by logos34 on 2008-01-10
I'd go with x64 ubuntu.  The packages are virtually identical to what is offered in 32-bit, and issues like flash, 64-bit codecs, etc. have been solved.  Head over to the x86_64 forum.  x64 is faster.  And you can address 4+ gigs of ram.

It's not necassary to reinstall vista.  Use vista's built-in disk managment tool to shrink it to make room for linux--don't use Gparted/let the ubuntu installer do it  (If you reinstall vista make sure to leave empty space for linux).  Grub should work fine as a dual bootloader.  But stuff happens and you can alternatively boot linux with vista boot manager using [EasyBCD]("http://neosmart.net/wiki/display/EBCD/linux").

Linux root should be ext3.  You can read+write to ext3 from vista using fs-driver, and you can write to vista/ntfs if you configure it to mount using the ntfs-3g driver.  (Gutsy comes with latter installed, but you need to configure fstab using the ntfs-config tool.  See below).

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

