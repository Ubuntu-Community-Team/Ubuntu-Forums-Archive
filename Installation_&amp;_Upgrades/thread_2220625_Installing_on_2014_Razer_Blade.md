---
title: "Installing on 2014 Razer Blade"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by mikelwrnc on 2014-04-28
Hi folks,

First time poster and relative nub when it comes to linux. I'm trying to install Ubuntu 14.04 on my brand new 2014 Razer Blade. I used the pendrivelinux.com Universal USB Installer to create a bootable usb for 14.04, and it shows up in the boot menu, but when I select it the screen goes black for a couple seconds (backlight on), then off for a couple seconds (backlight off), then it boots into Windows 8 as normal. I've poked around the BIOS but can't really see anything that seems pertinent to making the usb boot properly. Any troubleshooting suggestions? Thanks in advance!

---

### Post by m_duck on 2014-04-29
I don't have any *real* help per se, but it might be worth searching around secure boot and UEFI. I don't have any systems with secure boot, but modern laptops like the Blade will probably have it. Last time I saw it needed disabling or some bootloader magic to make it work with Linux.

Sorry it's not a proper answer, but hopefully a starting-off point to find such a thing! Good luck!

---

### Post by grahammechanical on 2014-04-29
The issue should not be anything to do with secure boot as Ubuntu is able to load the live session and install and run with secure boot on since 12.04.1. The system is failing to find an OS to load on the USB memory stick and that could because ... well read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]If you get a [/FONT][/COLOR]**Secure boot**[COLOR=#333333][FONT=Ubuntu] or [/FONT][/COLOR]**signature**[COLOR=#333333][FONT=Ubuntu] error, you may wish to disable [/FONT][/COLOR][SecureBoot]("https://help.ubuntu.com/community/UEFI#SecureBoot")[COLOR=#333333][FONT=Ubuntu] as described [/FONT][/COLOR][here]("https://help.ubuntu.com/community/UEFI#SecureBoot")[COLOR=#333333][FONT=Ubuntu], then retry to boot the disk. [/FONT][/COLOR]

Are you getting a secure boot or signature error?

Regards

---

### Post by mikelwrnc on 2014-04-29
Thanks for the tip! Indeed, googling led me to find that I had to change some settings associated with secure boot. Specifically, in the BIOS, under the "Boot" tab, I edited the "CSM parameters" section to have "launch CSM" enabled and made all other options "Legacy only" (not really sure if these are all necessary, but it works and has no detrimental effects otherwise).

---

### Post by mikelwrnc on 2014-04-29
Oh, next problem: the i386 version of 14.04 installs fine, but when I try to install the amd64 version I get a kernel panic on the first reboot after the installation. The error message is "Kernel panic - not syncing: No init found. Try passing init = option to kernel". Rebooting in advanced mode yields the following right before the kernel panic: "Starting init: /bin/sh exists but couldn't execute it (error -8)"

Any thoughts?

---

### Post by mikelwrnc on 2014-04-30
> **mikelwrnc said:**
> Oh, next problem: the i386 version of 14.04 installs fine, but when I try to install the amd64 version I get a kernel panic on the first reboot after the installation. The error message is "Kernel panic - not syncing: No init found. Try passing init = option to kernel". Rebooting in advanced mode yields the following right before the kernel panic: "Starting init: /bin/sh exists but couldn't execute it (error -8)"

Any thoughts?

Solved it. Re-creating the live USB using rufus instead of the pendrivelinux tool yielded an install that worked fine.

---

### Post by AAK on 2014-05-11
mikelwrnc, have you had any other issues or tips regarding installing and/or running 14.04 on your Blade?

---

### Post by Marjovsky on 2014-05-27
I'm thinking about buying a 2014 razer blade. Have you had other issues with 14.04 (for example mousepad issues, crashes or nvidia problems)? Do you think is a good buy if I will spend most of my time in ubuntu?

---

### Post by CavemanNinja on 2014-06-10
+1

I'm also seriously considering the new Blade but I need to know if Ubuntu will work. Like Marjovsky said issues I expect, trackpad, nvidia card, networking. Haven't been able to find much information from people who own the laptop. If I can check the Ubuntu box I can get this otherwise it's a Macbook Pro and I'm really not too keen on working in osx.

---

