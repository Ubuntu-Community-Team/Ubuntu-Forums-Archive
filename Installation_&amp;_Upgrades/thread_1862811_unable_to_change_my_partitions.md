---
title: "unable to change my partitions"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Smarty_T2 on 2011-10-17
Howdy,
I wanted to install ubuntu on my laptop so i downloaded the ubuntu dvd iso. Then i used the usb creator from linuxpendrive.com, created a partition on my hard drive (3 GB) and installed the iso on that partition. Now when i boot my system, i see the ubuntu loader and i cannot log into windows. Also, when installing ubuntu, i am not able to shrink my windows drive to create a partition for windows. Any help is greatly appreciated.
Thanks

---

### Post by zvacet on 2011-10-18
If you have Windows 7 then shrink existing partition from Windows.After that install Ubuntu on unallocated space.I think 3GB is too small partition for ubuntu.

---

### Post by kishanbhat on 2011-10-18
I think you replaced your windows bootloader with [www.**pendrivelinux.com](www.**pendrivelinux.com) **boot loader and that is why you don't see Windows boot menu.

Have you tried adding Windows boot option to your [www.**pendrivelinux.com](www.**pendrivelinux.com) **boot loader menu?

---

### Post by Mark Phelps on 2011-10-18
First thing you need to do is confirm that Windows is still there.  So, boot into Ubuntu, go to the "home" icon on the left, click it -- and confirm not only that the Windows partition is still there, but that it also has files in it.

If you see the files, then open a terminal in Ubuntu and enter "sudo update-grub". This will regenerate the GRUB menu and should add an entry for Windows.  Watch while it works and confirm that it finds Windows.

If that works, when you reboot, you should then see a GRUB menu, and when you select Windows, it should boot OK.

If all of that works, then you have Windows back.

Second thing to do is reboot into Ubuntu, open a terminal and enter "sudo fdisk -lu' (lowercase L, not a one).  That will list out the partitions on your drive.  Post the results back here.

Third thing to do is reboot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will come in very handy later, should you need to repair the Win7 boot loader from damage during your dual-boot installation.

---

