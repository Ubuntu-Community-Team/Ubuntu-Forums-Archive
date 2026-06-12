---
title: "No operating system found when trying to install from usb"
date: 2017-01-02
forum: Installation &amp; Upgrades
---

### Post by undeadartz on 2017-01-02
I'm trying install lubuntu on my pc. I make a bootable usb using the program "Pen Drive Linux" i try to install it but when i try to boot from the usb it temporarily pops up with "No operating system found" and boots straight into windows. I'd really like to install lubuntu but at this point it's basically impossible.
Some PC Info:
-Dell Inspiron 3847
-Ram: 16 GB
-HDD: 1TB
-Bios Version: BIOS Date: 06/29/15 14:15:48 Ver: 04.06.05
-Architecture: x64
Any help would appreciated. Thanks

---

### Post by yancek on 2017-01-02
Which version of windows do you have?  Newer (windows 8 and 10) use UEFI so you need to boot/install Lubuntu UEFI.  The BIOS on your computer will have different options.  Maybe reading through the Ubuntu documentation below will help.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by undeadartz on 2017-01-02
i have windows 10 and ive tried uefi and legacy i had windows 7 and it worked fine so idk why it'd not work on windows 10

---

### Post by yancek on 2017-01-02
Do you have another computer on which to test the usb to see if it boots.  Pendrive Linux usually works but there is no guarantee.  Testing on another computer would eliminate a failed write as a possible problem.

---

### Post by RobGoss on 2017-01-02
> **undeadartz said:**
> I'm trying install lubuntu on my pc. I make a bootable usb using the program "Pen Drive Linux" i try to install it but when i try to boot from the usb it temporarily pops up with "No operating system found" and boots straight into windows. I'd really like to install lubuntu but at this point it's basically impossible.
Some PC Info:
-Dell Inspiron 3847
-Ram: 16 GB
-HDD: 1TB
-Bios Version: BIOS Date: 06/29/15 14:15:48 Ver: 04.06.05
-Architecture: x64
Any help would appreciated. Thanks

How are you trying to boot that USB?

Have to changed your **BIOS** to use the** USB** as first boot? 

Did you hit the **F-12 **key on your keyboard to get the boot option to boot from the USB

It can be a number of things that are not being done to boot from the USB. Your machine will not just just boot off of the USB drive unless you tell it to and sometimes this may require making a few changes in the BIOS settings of your machine

Tell us what methods you're using to boot from the USB drive

---

### Post by undeadartz on 2017-01-03
Well, I've set my boot priority to USB and changed the bios to both UEFI and legacy but neither work. I've been able to install it on my PC before but that was before i upgraded to windows 10. I'm not sure if that has anything to do with it though.

---

### Post by oldfred on 2017-01-03
Do not mix UEFI & Legacy/CSM, only boot in UEFI mode. But some with Dell have mentioned they still have to turn on Legacy but boot in UEFI. 
Most systems either have UEFI on/off or Legacy on/off and then only boot in mode that is on.

Default install of Windows 7 is BIOS, but it can be installed in UEFI mode. But only if copied to flash drive and boot files moved & renamed to make it UEFI bootable.

Windows 10 has always on hibernation which must be off.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

I have a Dell 3647 with similar specs and it just worked, booting in UEFI mode. I originally installed 15.04, but since reinstalled with 16.04. But it primarily is Windows (now 10) just for TV use, that I cannot use Linux for.

---

