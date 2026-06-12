---
title: "Deleted ubuntu GRUB and cant install it from the BIOS"
date: 2014-11-10
forum: Installation &amp; Upgrades
---

### Post by rafael21 on 2014-11-10
A while ago I had installed Ubuntu 14.04 on a dual boot with Windows 8.1 on my Toshiba laptop .
What happened was that I uninstalled ubuntu to try  other distros of linux using a program called EasyBCD. 
This eliminated the GRUB ( choose if boot into ubuntu or windows ) and format the partition disk that contained it . 
It works, but when I tried to install other linux OS from my USb , I couldn´t enter the BIOS to choose to boot from drive (in my case USB )
Typically, when you turn on the laptop a brand logo appears with the message " press f2 for setup" or something like that.
 What it was saying when I installed Ubuntu for the first time , but now it no longer appears and does not enter the BIOS with any key (I tried all the F1- F12) .
Please , I'm almost new in ubuntu linux, and I want to install Ubuntu again and other oS.

---

### Post by oldfred on 2014-11-10
Is system UEFI or BIOS? Not really a Windows or Ubuntu issue but a UEFI configuration issue.

Some new systems have a fast boot in UEFI, where you skip the UEFI boot for faster booting. But then you cannot get into UEFI to reconfigure system. UEFI or BIOS normally spend a few seconds reviewing what hardware you have and then tell that to operating system for booting. But usually that does not change so a quick boot is skipping all that. You need to change UEFI setting before making any system changes.

My system has a setting for how fast and after error will let you get back into UEFI.

Often that error setting can be set by totally powering down system, remove battery if laptop. And hold power switch to drain residual power for a minute. Then on next boot you should be able to get back into UEFI with corect key for your system.

---

