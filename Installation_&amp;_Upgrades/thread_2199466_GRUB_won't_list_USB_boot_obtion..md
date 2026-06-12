---
title: "GRUB won't list USB boot obtion."
date: 2014-01-14
forum: Installation &amp; Upgrades
---

### Post by PotatoHead007 on 2014-01-14
So i got a Samsung NP3000C(or something like that), pre-installed with Windows 8. I want to keep it for Games, but i need Linux for work etc. 
I made a boot-able Flash drive. I have followed countless tutorials on disabling FastBoot, changing UEFI settings etc. But whatever i do, i only have the "Windows boot loader" as an option in boot priority. Does anyone know how i can make my BIOS recognize my USB?

---

### Post by carl4926 on 2014-01-14
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2014-01-14
Is this an older Samsung with UEFI, or a year or two old?
 If Samsung check model number as some can only be installed in legacy/CSM mode or computer may be bricked.
Kernel updates being released and Samsung needs to update UEFI/BIOS.

   UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
[http://mjg59.dreamwidth.org/25091.html](http://mjg59.dreamwidth.org/25091.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.

Newer systems or UEFI updates seem to resolve many of those issues.

---

### Post by PotatoHead007 on 2014-01-15
My PC is quite new, a series 3. I will check, and follow up on your links. Thank you.

---

### Post by oldfred on 2014-01-15
Some other newer Samsungs

  SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)
      
 How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

---

### Post by PotatoHead007 on 2014-02-01
Sorry for answering so late :/ I fixed it. Here is what i did(almost kicked myself for not doing it in the first place):
Used a Windows tool to Update BIOS. Now i could see all my USB ports, CD drive etc. 
Changed boot priority to USB. 
Went to boot menu with F10, booted Ubuntu.
Dual boot worked(i tried), but i deleted Windows later. Thanks for your help though :)

---

### Post by john235 on 2014-06-12
Hi,

I have the opposite problem. I have Ubuntu 14.04 on a Surface Pro 2. I am trying to run Gparted Live from a Live USB, but the grub doesn't show the USB. Any ideas?

Thanks in advance everybody!

---

### Post by yancek on 2014-06-12
Grub won't show a LiveCD on a flash drive.  You need to enter the BIOS (setup) and change the boot priority to boot from the flash drive.  Different machines use different keys so watch the first screen on boot.

---

