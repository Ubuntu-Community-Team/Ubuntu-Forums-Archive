---
title: "Trying to load ubuntu after HDD replacement.  *first timer*"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by itsjunkbill on 2015-09-26
Was running VMs in Windows on a Intel I3 2.20 GHZ NP300 from Samsung. My HDD was constantly maxing out so I decided to replace it and since I had recently upgraded to Windows 10 I figured that instead of going through the hastle of trying to transfer my windows licence I would just install Ubuntu. 

Tried to burn .iso to a double layer DVD but then I wasnt sure that my disc reader would be able to read it. Dumped the .iso onto a flashdrive and replaced the HDD ( old one was 5400RPM new one is 7200RPM so I was thinking that might have something to do with it as well?) Can get into the bios however when I get to the boot menu there is nothing on it? 

Then all the PC does is flash on and off and on and off and on and off again with a black screen. I can get to the bios, it sees the HDD. I also tried to administratively take down everything but the USB still not having any luck. 

When I was using the disc it seemed like it wanted to do something, I could hear it working ( possibly trying to read the disc? ) however there was never any progress menu or anything. No command prompt? 

What am I doing wrong?

---

### Post by grahammechanical on 2015-09-26
Let us think about this. A new hard disk without an OS and the motherboard is trying hard to find an OS on the drive and it has no where else to look. That sound like the situation? Was Windows 8.1 pre-installed on this machine? If so you will have a UEFI boot system. The UEFI menu will not see the OS on the USB stick because you need to change some setting to tell the UEFI to look at a USB port for an OS.

I cannot tell you how to do that as my machine has a BIOS boot system. There should be settings for USB and there should be settings for hard disks. On my BIOS system a USB stick with an OS on is seen as an externel USB drive. And I can give it priority over a hard disk in the section of the BIOS for Boot, sub section Hard drives.

Regards.

---

### Post by SuperFreak on 2015-09-26
> **itsjunkbill said:**
> 
Tried to burn .iso to a double layer DVD but then I wasnt sure that my disc reader would be able to read it.


see [http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

> **itsjunkbill said:**
>  Dumped the .iso onto a flashdrive and replaced the HDD ( old one was 5400RPM new one is 7200RPM so I was thinking that might have something to do with it as well?) Can get into the bios however when I get to the boot menu there is nothing on it? What am I doing wrong?



see [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by itsjunkbill on 2015-09-28
Thanks for the quick responses, after doing some research on Youtube I found out that the .iso needed to have the file converted to be bootable. I used pendrive linux like posted by SuperFreak and was able to load without an issue. 

Thanks!

---

