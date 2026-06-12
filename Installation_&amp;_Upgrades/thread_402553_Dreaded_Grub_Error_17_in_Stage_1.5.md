---
title: "Dreaded Grub Error 17 in Stage 1.5"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by ZakMckrackin on 2007-04-05
Ok, I have Windows XP installed on this computer first and I have installed ubuntu 6.10. When I try to boot up to go to the Grub Menu i get:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

Been trying to fix it for the past day and a half. Anyone can help?

---

### Post by confused57 on 2007-04-05
> **ZakMckrackin said:**
> Ok, I have Windows XP installed on this computer first and I have installed ubuntu 6.10. When I try to boot up to go to the Grub Menu i get:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

Been trying to fix it for the past day and a half. Anyone can help?

Boot up the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

The live cd can also be used to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ZakMckrackin on 2007-04-05
```
Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       16708   134206978+   7  HPFS/NTFS
/dev/hda2   *       16709       36418   158320575   83  Linux
/dev/hda3           36419       36483      522112+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666    7  HPFS/NTFS
```


Tried the re-install but when i did the find /boot/grub/stage1 i got Error 15: File Not Found :mad: .

---

### Post by confused57 on 2007-04-06
Do you have access to another computer or can boot Windows?  If so, you might want to download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Here's a description of grub error 17:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

Hopefully, the SGD will enable you to boot Ubuntu & is also capable of booting Windows or restore your Window's IPL code to the mbr.

Is hda1 your Window's install?

---

### Post by ZakMckrackin on 2007-04-06
Yea hda1 is Windows XP Home Edition,  Just made the SGD Disk hopefully I can sort this out rebooting wish me luck!

EDIT: I just realized that i cant create a SGD CD due to the rest of the computers in my household are all Windows Xp....either that or I am doing it wrong. Is there any way to get an SGD from a Windows computer?

---

### Post by confused57 on 2007-04-06
> **ZakMckrackin said:**
> Yea hda1 is Windows XP Home Edition,  Just made the SGD Disk hopefully I can sort this out rebooting wish me luck!

EDIT: I just realized that i cant create a SGD CD due to the rest of the computers in my household are all Windows Xp....either that or I am doing it wrong. Is there any way to get an SGD from a Windows computer?
You should be able to with no problem, if you have cd/dvd writing software installed, which you probably do if you have a cd/dvd writer.  Just use your cd writing software & burn the iso "as an image" or something to that effect, don't burn as data or a bootable disk...burn it at no more than 8X write speed.

---

