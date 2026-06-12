---
title: "Need help with GRUB"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by RasterBurn on 2010-05-01
hello, i did the upgrade from 9.10 to 10.04 and unfortunately it ended up breaking grub, rebooting brought me to a line that says "grub rescue>"  this was totally screwy for me as i have never seen it, anyways, so i put in my 9.10 live disk and reinstalled 9.10, simply resizing my boot partition (sda1) and creating a 20gb partition (sda3) to install 9.10 on along side of the boot partition I was able to get things running again but unfortunately i have only a couple problems that need to be straightened out in the boot loader...

first i would like to make a copy of the boot loader and put it onto a cd to boot into the OS from in case something goes wrong and i cant boot into the OS any more (maybe boot into sda3)

second i would like to either change the current default boot from sda3 to sda1 (tried changing "default = 0" to "default = 4" and running the update-grub command but it didn't have any effect on the bootup) or else get grub2 to work from Ubuntu 10.04 so that i don't need to change over to the right kernel at the bootloader when i turn on the computer as sda1 is my primary partition containing 10.04 with all my files and setting

---

