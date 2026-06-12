---
title: "Ubuntu installation not working on Z97 Pro MoBo."
date: 2017-03-13
forum: Installation &amp; Upgrades
---

### Post by misterc006 on 2017-03-13
Just completed my first build and have messed with Ubuntu in the past but am still a noob, so I am trying to install Ubuntu on my computer. It has no operating system and a Z97 Pro gamer motherboard. I made a flash drive with Ubuntu 16.04.2 LTS ISO and plugged it into the computer, but when I tell it to boot the flash drive, the screen flickers a bit and then just returns to the BIOS screen. Any help? I already disabled secure boot and removed the boot keys.

---

### Post by mörgæs on 2017-03-14
Hi, welcome to the fora.

I don't know this particular motherboard but a brief googling indicates that it's new. Have you tried a live boot of 17.04 (beta)?

---

### Post by oldfred on 2017-03-14
What brand motherboard & then what video card or Intel chip for video?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

### Post by misterc006 on 2017-03-15
Sorry for the late reply, 

Asus Z97 Pro Gamer

GTX 1060

Intel Xeon E3-1231



No I haven't tried the live boot. As this is my first time using Linux on a desktop, I wanted to keep it simple with the latest release.

---

### Post by oldfred on 2017-03-15
You probably need nomodeset to initially boot and until you install the nVidia proprietary drivers from Ubuntu's repository.

Some issues are by brand, and others by model like X97.
 Gigabyte GA-Z97MX-Gaming 5 with MSI GTX 970 CSM must be disabled
[https://ubuntuforums.org/search.php?searchid=14566915](https://ubuntuforums.org/search.php?searchid=14566915)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu) 

  Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)

---

