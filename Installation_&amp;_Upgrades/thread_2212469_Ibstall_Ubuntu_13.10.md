---
title: "Ibstall Ubuntu 13.10"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by IMNemo on 2014-03-21
I am running an HP Pavilion dv7 laptop with 2 hard drives (sda, sdb).  I want to install Ubuntu 13.10 64bit on sdb, at present I have Windows 7 64bit booting on sda.  My question is:  If I install 13.10 64bit on sdb, will the boot partition that boots W7 see 13.10 on sdb?  If not, can it be made to do so?  A friend told me that what I'm trying to do will not work.  Of course he isn't sure why it won't work or how to fix it.  If I have not given enough information, or if what I have given isn't clear, please ask me, and I will try to provide a better explanition.  Thanks for all of your help in the future.

---

### Post by ajgreeny on 2014-03-21
Im many ways you have the best situation possible with two physical hard drives, one of which can stay untouched as windows, the other can hasve ubuntu installed but will offer the option to boot to either OS..

I recommend you back up any data files on sdb and then install ubuntu on to that drive.  It is important that you choose "Something Else" at the partitioning stage of the install and you are then able to choose to put the bootloader files of ubuntu on /dev/sdb (note, not to a partition but to the root of the drive, just sdb).

This means that the bootloader for Windows on sda will be untouched so if you leave sda as boot priority device the mechine will boot straight to Windows.  If you change the boot priority to sdb in the BIOS you will go to the grub menu and should be able to choose to boot either to ubuntu or to windows.

It is possible to arrange a shared ntfs partition on one or both hard disks if you want to, but we would need to know what is on both disks now before giving you any further recommendations about that, so before you actually install, boot to the live ubuntu OS from the install DVD or USB, open gparted and show us screenshots of both hard disks, which you can get to from the dropdown box top right of gparted.

---

