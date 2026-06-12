---
title: "dell inspirion 17 5767 remove factory loaded win10 (sole boot) and replace with 16.04"
date: 2017-12-13
forum: Installation &amp; Upgrades
---

### Post by edithto on 2017-12-13
1. I see very little. I use laptop for own work, offline. need camera, mic, scanner, multi-media editing capability, ....with occasional online transfers. is 16.04 best choice?

21. 5767 dell laptop is not on canonical list. I have used win10  'troubleshoot' to 'remove' win10. But no screen. how to get screen to  access boot menu?

3. if yes, what alternative to rufus best, to create bootable usb offline for 16.04?

---

### Post by oldfred on 2017-12-13
The 16.04.3 may be ok, or 17.10, but then you will have to upgrade to 18.04 when it comes out next April.

Ubuntu/Linux is not Windows. While it can do most things, it cannot run Windows software and new software (even Windows) has a learning curve.
Best to dual boot if not already an Ubuntu user.

My older Dell wanted several backups, Windows backup, Dell backup, and I made a full image backup with Macrium.
 [http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp) 

Suggest backups as many users find one application or game they must have that only runs or runs well in Windows. Or later want to sell system and need Windows on it to sell it.
One user posted he buys system with HDD, immediately uninstalls HDD and adds better SSD. Then later sells system with "new" unused Windows on HDD, so he can upgrade to newer system. Much better performance with SSD.

If you have not already made Ubuntu installer you cannot from UEFI boot menu. Most Dells use f12, but many systems have other keys for boot menu, but you have to have a bootable drive. You may want to turn off UEFI Secure Boot, and Dell seems to be unique that it wants CSM/Legacy/BIOS on, but you still can and should boot in UEFI mode. Most systems with CSM on, only boot in BIOS mode. And boot of flash drive is separate from boot of internal hard drive. You just need to be consistent and always boot in UEFI mode.

      
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.57809194.1251095709.1512369991-1898146045.1512369991#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.57809194.1251095709.1512369991-1898146045.1512369991#0)
      
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

