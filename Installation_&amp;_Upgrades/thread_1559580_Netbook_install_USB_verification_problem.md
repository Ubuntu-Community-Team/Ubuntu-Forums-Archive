---
title: "Netbook install USB verification problem"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by ajgreeny on 2010-08-23
I currently have Ubuntu 10.04 on my netbook  (Novatech X10) and am looking to try Mint 9 isadora, just to compare  them. I can run the isadora live USB stick with no problems of any kind,  but simply thought I would check the media from the boot menu system,  "Check installation media/CD" or whatever the exact words are. The USB is  checked, and everytime it reports in real time that 4 files are missing  from isolinux, then checks through the casper filesystem, and finally  tells me "4 errors were encountered, press enter to reboot".  I presume  these errors are the missing files, which are:- 
/isolinux/isolinux.cfg 
/isolinux/splash.jpg 
/isolinux/memtest 
/isolinux/vesamenu.c32 
However, I see all 4 of those are in /syslinux, not /isolinux, so I just wonder if this is a quirk of the system in some way. 
 
Can somebody tell me if this is normal in USB installation media, I  always check my CDs this way before using them to install but have never  done it with a USB install disk before. The iso is OK, as it was  checked with md5sum. I am reluctant to use this USB to install in case  there is a problem, but I would like to know if this is simply a USB  problem and the install should go OK, or if I should "burn" the USB  again, perhaps with unetbootin, instead of the ubuntu Startup Disk  Creator. 
 
I have posted this question in the Linux Mint forum as well so hope I will get an answer from somewhere.

---

