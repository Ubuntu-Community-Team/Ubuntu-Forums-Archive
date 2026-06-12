---
title: "Clean install ubuntu, only GRUB commandline shows up"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by viebboy on 2015-02-11
Hi,
Is there anybody out there?
Just nob if you can here me..

Im just kidding, I bought a new notebook acer aspire e11 yesterday with preinstalled windows 8.1, I go straight to install ubuntu 14.04 , I create partition as instructed in this link 
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
However, when clicking install, theres warning message that I have to create boot partition ( not /boot) and define it as EFI mode. I gave it 200mb. However, after install, there is no bootable device, only grub commandline appear. I logged into bios and setup my only hard disk as first priority, but its still remains. 

I tried boot-repair with recommended options, but situation still the same. 
Heres the diagnostic result
[http://paste.ubuntu.com/10178359/](http://paste.ubuntu.com/10178359/)

Anyone help me please

UPDATE : after disable security boot, when I press power button, the computer displays message : default boot device missing or boot failed....
I press enter and then boot manager appear
1st option is unknown device (WDC WDxxxx)
2nd option is Windows boot manager (WDC WDxxx, same number as above)
I choose 1st option and I can boot into GNU GRUB

Anyone can show me how to set default boot device, it seems like bios does not recognise my hard disk as default boot device

---

### Post by oldfred on 2015-02-11
I am not sure if Acer is one of the mfg. that only boots Windows and requires a work around.

Did you intend to erase Windows as you only have Ubuntu?
Better to have followed UEFI install examples.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

      
 Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)


 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

      
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by viebboy on 2015-02-11
I would like to keep only ubuntu. 
I could boot into ubuntu but only after the familiar blue screen turned up and dislayed *default boot device missing*, after this message, it display boot manager and 1st option is my hard drive but with unknow device, I chose this option and it booted into familiar GNU GRUB boot manager.

---

### Post by viebboy on 2015-02-11
I checked and it says my ubuntu is installed in EFI mode and EFI boot on HDD

---

### Post by oldfred on 2015-02-12
Some of the other threads on Acer similar models say you have to set password to allow you to make some settings.
But if you do have to set password, do not ever lose that password.

---

