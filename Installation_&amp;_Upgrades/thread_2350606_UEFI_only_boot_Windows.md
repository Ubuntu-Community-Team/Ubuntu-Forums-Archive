---
title: "UEFI only boot Windows"
date: 2017-01-25
forum: Installation &amp; Upgrades
---

### Post by hopek2 on 2017-01-25
Hello everyone,


I would like to install Lubuntu on my Lenovo Ideapad 100S. I have prepared bootable USB with Lubuntu 16.04 (x64), using Universal USB Installer and disabled Secure Boot.
In my UEFI I cannot change boot order nor switch to Legacy mode. When I pressed f12, among Efi Boot Devices there is only Windows Boot Manager.
I tried to use EasyUEFI to manually create new entry and change the boot order, added /EFI/BOOT/BOOTx64.efi as a file path. When I restart, I get the message "Lubuntu boot failed" so it didn`t help.  
Does anyone have any other ideas? 

Regards,
Mat

---

### Post by yancek on 2017-01-25
Are you trying to install Lubuntu?  If so, you do not want to change to Legacy if you have windows 8 or 10 as they use UEFI.  If you have one system using UEFI,you need to install any other system UEFI or it will be nothing but trouble.  Take a look at the link below on dual-booting windows UEFI with Ubuntu.  You might also post info on your hardware, specifically the manufacturer of the computer as the method for making these changes varies with manufacturer.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by hopek2 on 2017-01-25
Yes, I am trying to install Lubuntu. The problem is, that I cannot boot antyhing else but Windows Boot Manager. 
Specs:
Lenovo Ideapad 100S-11IBY
Intel Atom CPU Z3735F @1.33GHz, 4 cores
Bios Version Lenovo E2CN14WW 23.09.2016
Mainboard Aristotle 11.6
2GB RAM

---

### Post by igdfpm on 2017-01-26
You do not need to "manually" create a boot entry for lubuntu at all as it will be automagically created as part of the installation.

Your post is very confused... have you installed Lubuntu to your harddrive from the USB or are you attempting to boot the USB (using EasyUEFI????)

---

### Post by hopek2 on 2017-01-26
Sorry for confusing, I`m not very experienced user. No, I haven`t installed Lubuntu, I just can`t boot the USB.

---

### Post by igdfpm on 2017-01-26
USB sticks failing to boot on a UEFI machine is quite common.

1) Boot into windows
2) Disable hibernate + fast start (it can cause all manor of linux woes including boot problems)
3) plug in your usb
4) hold down shift button while clicking "restart" to access windows start up options
5) when it boots to blue options screens select "Troubleshoot" -> "Advanced" -> "UEFI Settings" then select UEFI Setup Menu
The machine will again restart into the UEFI menu
6) Find the Boot Options section of your UEFI menu and make sure your USB stick is listed and at the top of that boot order list.
7) SAVE the changes in the UEFI menu and restart your machine - you should get the lubuntu install menu.

I personally would boot into a live session and use gparted to resize my main windows partition and precreate any partitions I will be using for linux - one big one is fine, but a separate home is useful ;)

You should then be able to install lubuntu from the live session - when it comes to selecting a partition for the bootloader select the existing EFI partition BUT DO NOT mark it for formatting.

Enjoy ;)

---

### Post by oldfred on 2017-01-26
Vendors/Microsoft created some lightweight systems that boot in UEFI 32 bit mode only and have no BIOS boot mode or are UEFI class 3 devices.
That was back when Linux did not have a 32 bit UEFI and they were trying to make a Windows only system. 

Then Linux did develop the 32 bit UEFI, so it is possible but not exactly easy.
[http://askubuntu.com/questions/684041/ubuntu-debian-on-a-lenovo-ideapad-100s-linux-has-issues-with-this-laptop](http://askubuntu.com/questions/684041/ubuntu-debian-on-a-lenovo-ideapad-100s-linux-has-issues-with-this-laptop)

There are now sources for bootia32.efi to boot with instead of the standard 64 bit versions.
Older threads mention compiling your own. Multiple sources, this mentions one.
[http://askubuntu.com/questions/392719/32-bit-uefi-boot-support](http://askubuntu.com/questions/392719/32-bit-uefi-boot-support)

---

### Post by hopek2 on 2017-01-29
Thanks for your answers guys, 32bit UEFI was the problem. 
I have downloaded Lubuntu with 32bit UEFI from Linuxium website, it boots and install without any problems. 
The author says that patches that fix common issues (no sound, no power managment) are already implemented- unfortunately I still have those problems on my computer and it looks like it is pretty diffcult to fix. 
Anyway, if someone has similar issues with booting, it is worth a try :)

---

