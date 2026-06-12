---
title: "Dell Inspiron 15R giving me install trouble"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by dysin187 on 2013-12-22
I lurked around reading all the posts that mentioned win8, uefi, and 15R's in general and tried to follow the directions given to others best i could. I was trying to resolve why even though it allowed me to install & customize ubuntu 12.04 along side win8, i couldn't get the dual boot screen that lets me choose which one to use upon start up. I retried multiple installs and then moved to the boot repair tool after checking that the bios seemed to match the reccomended settings. At first it would just continually boot straight into win8 but after running boot repair now that doesn't even happen, neither os is showing available now. Boot repair provided this url: [http://paste.ubuntu.com/6597547/](http://paste.ubuntu.com/6597547/)

I would just give up and wipe everything and run ubuntu solo however, i just bought this laptop with light gaming as a priority and have already installed skyrim & the star wars mmo and would rather not have to re-download and install those.

---

### Post by oldfred on 2013-12-22
Welcome to the forums.

Some very new UEFI systems work a lot better with 13.10. The new 12.04.4 that will be out in Jan will have even more improvements but the 12.04.3 is now getting behind.

It looks like you have dual video both Intel & Radeon. I do not know about that.

It looks like you have this issue:
>  Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). 

Sometimes runing chkdsk from Windows may repair it, but usually you have to backup the entire efi partition, totally delete it and then with gparted recreate it as FAT32 and with boot flag as that makes it the efi (ESP) partition. Then copy Windows files back and rerun Boot-Repair. 
Do not accept the option to rename files (yet). That is for some UEFI that will only boot the Windows UEFI entry. If you can boot ubuntu entry from UEFI (once it gets created) then you do not need the rename.
 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)

 
The Dell's seem pretty common across versions. With 12.04 you may need sputnik, but all those updates are in the 13.10 version. I do not know differences across various models.

 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)

---

