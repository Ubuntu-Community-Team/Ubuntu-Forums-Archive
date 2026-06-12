---
title: "Grub not able to overwrite Windows boot loader"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by markjo on 2011-03-17
I tried to install linux on hard disk and it installed without any problem. However, when i boot i directly get the windows boot loader screen and no grub screen.

I reinstalled linux. I tried to fix grub, but still no grub screen.

Please help.

---

### Post by stlsaint on 2011-03-17
It looks like you have grub installed to a partition instead of the MBR on the drive. Please follow the link in my signature titled bootinfoscript so that we can get more info about your drive setup. (also looks like you have two seperate installs of linux on sda6/7. After you run the script you will get a output txt file called Results.txt. Please attach that file to this thread.

---

### Post by markjo on 2011-03-17
> stlsaint wrote:
(also looks like you have two seperate installs of linux on sda6/7.

There is only one linux OS installed. It is showing Linux for the type of partition.

---

### Post by stlsaint on 2011-03-17
>  => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

Double check to ensure that bios has your sda drive (linux) set as the drive to boot from and not sdb.

---

### Post by markjo on 2011-03-17
I am able to boot into linux now. On clicking the windows option, i am taken to the windows boot option screen. But, the XP option does not work, the PC reboots. 

Any idea how that can be fixed?

---

