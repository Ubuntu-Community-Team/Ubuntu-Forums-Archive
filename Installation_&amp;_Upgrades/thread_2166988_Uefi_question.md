---
title: "Uefi question"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by macstl on 2013-08-11
If I buy a new laptop will unbuntu 12.10 or higher install without intervention? If not what needs to be done? Anything more than turn off secureboot in bios?
I want to clone img the win8 with clonzilla and install just ubuntu.

---

### Post by oldfred on 2013-08-12
You need to turn off fastboot or hibernation in Windows (and UEFI if in it also). You can boot UBuntu with secure boot on, but usually best not to. But check that Windows still boots with secure boot off. Some have to have secure boot.

Shrink Windows using Windows disk tools to make room for Ubuntu. Create Windows 8 repair flash drive and backup a image of Windows & efi partition or know if recovery is an automatic one key type.

Then Ubuntu should install, but os-prober has a bug and you have to run Boot-Repair to fix the menu.

See also my signature for more detail and lots of useful links.

Video on UEFI install after Windows install.
       Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)

---

### Post by macstl on 2013-08-13
I don't want to keep windows. I want no dual boot just a complete Ubuntu 12.10 or higher. What extra things I have to do besides std install because of uefi?

---

### Post by oldfred on 2013-08-13
UEFI also has CSM or BIOS mode. So you have a choice of the 30 year old BIOS mode which most understand, but is being phased out. Or install in the new UEFI mode.

If an Ultrabook or very high end system, then there are more steps to remove RAID meta-data on drive and configure dual video. Otherwise it should install. Some low end laptops seem to have very limited UEFI and are only designed to work well with Windows. Best to stick with the major brands and better but not necessarily the best models.

Links to several different brands and users who installed Ubuntu. A couple have removed Windows. 

I suggest you keep Windows as dual boot until you know it works. Or as one user previously suggested. Buy a system with a hard drive, but remove hard drive with Windows and totally replace with a SSD and install Ubuntu. Then when you sell computer later you can reinstall the Windows drive.

---

### Post by macstl on 2013-08-14
I got my eye on a Lenovo - IdeaPad laptop model N585. $300.00 What do you think of it for Ubuntu? I have had good experience with 2 Lenovo thinkpads older version, everything works with Ubuntu. You said some low end laptops with uefi are only designed to work only with windows, who is in bed with who on this? Microsoft and Intel , Microsoft and some regulatory agency or both?

I upgraded my first thinkpad to a T61 in order to get Unity to work. Maybe I should just stick with this until I'm force to upgrade again for some other new feature.

---

### Post by oldfred on 2013-08-14
Just like Apple Ipads are Apple only Windows has RT models that are Windows only. That is why the price of RT models are dropping a lot and Microsoft took a huge write down on inventory.

Reviews as a Windows computer seem mixed. Do not know how well it may work with Ubuntu.
[http://www.amazon.com/Lenovo-IdeaPad-Dual-Core-processor-Built/product-reviews/B00A96ROAE/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1](http://www.amazon.com/Lenovo-IdeaPad-Dual-Core-processor-Built/product-reviews/B00A96ROAE/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1)

[http://www.ubuntu.com/certification/make/Lenovo/?page=1](http://www.ubuntu.com/certification/make/Lenovo/?page=1)

---

