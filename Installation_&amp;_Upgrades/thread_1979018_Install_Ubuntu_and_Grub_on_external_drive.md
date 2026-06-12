---
title: "Install Ubuntu and Grub on external drive"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by Coastalguy on 2012-05-12
I would like to install Ubuntu and Grub on an external drive, thinking that if I set BIOS to have the external drive boot up before the Windows hard drive, I could just turn off the external drive which would then be by-passed and boot up Windows normally with it's mbr on the sda disk.

If this is possible, can someone explain the steps I need to follow to do this?

thanks,

---

### Post by wilee-nilee on 2012-05-12
Yes, when you install to the external use the something other option in the install gui, and make sure the grub bootloader goes to the externals mbr.

---

### Post by ajgreeny on 2012-05-12
Choose "Something else" at the disk preparation stage of installing, and all the disks available will be scanned.  You can then choose the disk you want, and also make the partitions necessary for your purposes.  you can also make sure that the bootloader system (grub) goes to /dev/sd[COLOR=Red]x[/COLOR] [COLOR=Black]where sdx is the external drive.  Do not put grub on a partition but on the mbr of that drive.[/COLOR]

---

