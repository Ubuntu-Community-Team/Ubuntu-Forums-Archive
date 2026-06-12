---
title: "USB Live Stick Not reaching Purple/Black Screen"
date: 2014-03-11
forum: Installation &amp; Upgrades
---

### Post by softwaregoddess2 on 2014-03-11
Hi,
I have a SanDisk Cruzer Pop 16GB USB stick loaded with Ubuntu Live 13.10 (Same results when I tried 12.04 LTS). The stick boots correctly on my Ubuntu 12.04 laptop, my RedHat6.1/MRG2.0 machine and a Windows 7 laptop but on a Intel Atom running an Intel Graphic card; it never reaches the 1st splash screen. I am using HDMI out to a Dell monitor. I know the USB slot and the display works because I loaded windows 7 from a USB stick using the same USB slot, and display. The system is using the AMI BIOS; the code where is seems to be toggling between is 0x62(Installation of the South Bridge Runtime Services) and 0x69(North Bridge DXE intialization started) and it appears like the system might be rebooting. I have tried modifying the /boot/grub/loopback.cfg and the /isolinux/txt.cfg with no change. So far I have tried 1) nomodeset,  2)acpi=off 3)Removing splash and quite. It is still booting on my Ubuntu 12.04 laptop, my RedHat6.1/MRG2.0 machine and a Windows 7 laptop but still no love on the ATOM. I am not sure I am even getting to where the config files kick in. 

Thanks,

---

