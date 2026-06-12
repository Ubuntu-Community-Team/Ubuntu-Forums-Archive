---
title: "Multiboot issue: Ubuntu (Legacy BIOS) and Win8 (UEFI BIOS)"
date: 2015-08-11
forum: Installation &amp; Upgrades
---

### Post by facundo6 on 2015-08-11
Hello! I am a WIN8.1 user that wanted Ubuntu installed on the laptop using dual boot (an approach I have used in the past with other versions of Linux and Win). My laptop is ACER Aspire E1-531-4697 with 4GB RAM btw.

To start off, I made space in the HDD partition, downloaded Ubuntu ISO and also the USB Installer from [www.pendrivelinux.com](www.pendrivelinux.com) which in turn asked me for the Ubuntu ISO of course so it could create the USB Boot drive. So far so good. 

BUT when I rebooted my laptop with the USB pendrive in, it ended up in an infinite loop of ACER logo, reboot, ACER logo, reboot, and so on instead of actually booting from the USB pendrive. So I checked on the laptop BIOS and decided to give it a shot at changing from "UEFI" to "LEGACY BIOS" boot mode. This worked like magic and the pendrive did bring up the installer and I successfully set-up linux on my new partition while keeping WIN8.1 alive in the old partition.

The problem I have now is that I haven't been able to get the Boot Menu setup, and the only way to select whether I want to use WIN or UBUNTU is to actually go into the laptop BIOS and select "UEFI" and reboot when I want to run WIN8.1.... or else go into the laptop BIOS and select "LEGACY BIOS" and reboot when I want to run UBUNTU.

I tried running boot-repair from within UBUNTU but it requires to run in UEFI mode - which I have proven doesn't work in my laptop for some reason (I even tried from CD instead of USB and it does boot but then says that boot-repair needs to run in UEFI mode and "from USB instead of DVD", go figure!). I have also tried running EASYBCD from within WINDOWS, which does let me set up a nice boot menu to select WIN or UBUNTU, but which doesn't work in the end for LINUX and presents different error messages no matter how I set it up. At least EASYBCD didn't break WIN8.1 boot and I was able to revert the changes it did.

I run boot-repair report and I can share with you folks for further input: [http://paste.ubuntu.com/12053463/](http://paste.ubuntu.com/12053463/)

Can you please help me? To begin with it "seems" that I have WIN8.1 on UEFI and UBUNTU on LEGACY BIOS - which I didn't even think was possible lol. All I want is a functional boot menu so I don't have to go into the BIOS setup all the time. 

Thank you so much!

---

### Post by grahammechanical on 2015-08-11
Ubuntu has not broken Win 8.1 boot. We cannot have it both ways. If Windows 8.1 is installed in EFI mode then Ubuntu must be installed in EFI mode. Otherwise we get the situation that you describe. Furthermore, to install Ubuntu in EFI mode we must run the Ubuntu installer in EFI mode. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2015-08-11
Acer requires you to set a supervisor password. Many threads on installing to Acer. Similar issues on all models:

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)

 Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
      
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

