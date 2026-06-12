---
title: "Having Trouble with Install"
date: 2016-08-18
forum: Installation &amp; Upgrades
---

### Post by amahoro on 2016-08-18
Hey guys.. I recently downloaded Ubuntu and created a live USB.. The drive booted up once now I get this image:
[ATTACH=CONFIG]270736[/ATTACH]

This happens after I press the "try Ubuntu" option. I cannot get on to the disk to type in any commands so therefore I have no idea what to do..

Here are the specs of my PC:
Gigabyte motherboard (DS3P)
Nvidia GTX 960
1 Kingston SSD
1 Western Digital Drive
8 GBs of RAM
AMDx64 8110 CPU x8 Core

---

### Post by walken on 2016-08-18
Hi Amahoro,
Have you any other boot entry on your usb bootable device ?
For example test the media or maybe install in OEM...
Best

---

### Post by amahoro on 2016-08-18
Well it did bit up once so I'm assuming the driver and file are fine. As for oem doesn't work. There's nothing else on the drive besides the ISO files

---

### Post by oldfred on 2016-08-18
With nVidia you normally need nomodeset both to boot live installer and install until you add the nVidia driver from repository. Do not download directly from nVidia.

Are you booting in BIOS or UEFI boot mode?
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

In BIOS mode you get tiny icons at bottom for just a few seconds and must press the famous "any" key. Then f6 to add nomodeset.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown and other boot parameters
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by amahoro on 2016-08-19
After replacing "quiet splash" with "nomodeset" I just get a black screen.. I fixed it.. turned out the install didnt like my usb.. You can now mark this as solved. Thanks for all your help guys :)

---

