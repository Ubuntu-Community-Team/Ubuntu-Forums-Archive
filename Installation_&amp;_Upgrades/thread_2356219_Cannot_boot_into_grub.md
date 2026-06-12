---
title: "Cannot boot into grub"
date: 2017-03-21
forum: Installation &amp; Upgrades
---

### Post by husin on 2017-03-21
hello im trying to install ubuntu on my laptop i want to install it alongside with windows 10 UEFI the instalation was sucsefull but i cant boot into grub, ive tried using boot repair installing grub manually but still cant and  cant even accses it in legacy mode but i installed it uefi mode (i think cause i use rufus and i set it to bios and mbr uefi) ive tried everything i know any help would be okay please help me im in need of using ubuntu

ps. right now im very frustirated cause of this 

My laptop is acer aspier e14 e5 457g 531g

---

### Post by alexandari on 2017-03-21
Get a USB drive and burn SuperGrubDisk to it. It's a utility that detects GRUB and lets you boot into the system if there is any problem. Start from here, try to boot into your ubuntu and then try to reinstall and debug. 
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) You can refer to ths

---

### Post by oldfred on 2017-03-21
Make sure you have latest UEFI from Acer. Some older threads mention downgrading UEFI, but newer threads say newest works.
And Acer has an unique requirement of inside UEFI setting a supervisory password and then enabling "trust" on the ubuntu/grub .efi boot file in the ESP.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

