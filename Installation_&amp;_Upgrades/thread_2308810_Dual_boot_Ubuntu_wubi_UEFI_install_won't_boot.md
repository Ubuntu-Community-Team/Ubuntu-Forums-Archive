---
title: "Dual boot Ubuntu wubi UEFI install won't boot"
date: 2016-01-05
forum: Installation &amp; Upgrades
---

### Post by waxcan on 2016-01-05
Hi folks,
No logs to hand I'm afraid.

I've installed Ubuntu (ubuntu-15.10-desktop-amd64.iso) using the latest wubi (1510) on my single partition Windows 10 drive with UEFI and secure boot off.

It comes up as a choice on boot when I enter startup options under UEFI, but when selected the machine just reboots and boots to Windows.

Does this sound like an obvious mistake somewhere?

I tried to install using unetbootin and a USB, but after a few attempts (each installed to the same new but cheap USB stick) it says 'no operating system found' or similar.  I've never used wubi before and previously installed using a stick. That said I think I always used BIOS over UEFI but Windows is already installed.

Cheers!

---

### Post by leunam12 on 2016-01-05
The best an easiest course of action is to run boot-repair, but you need a live USB.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by waxcan on 2016-01-05
Thanks, I'll give it a rattle right now :)

---

### Post by oldos2er on 2016-01-05
Wubi is no longer supported, and hasn't been for some time. I don't know why wubi.exe still exists in the *.iso, nevertheless we try to discourage its use.

---

### Post by yancek on 2016-01-05
The Ubuntu wubi page explains your problems.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Bucky Ball on 2016-01-05
*Thread moved to **Installation & Upgrades**.*

Forget Wubi. As mentioned, not supported. You'll get very little/no help with it (it is no longer supported here or by Canonical) and a Wubi install is not a dual-boot. :)

Do a clean install of a supported release. We can help you with that.

---

### Post by waxcan on 2016-01-05
Thanks. I used wubi to uninstall ubuntu (which wouldn't boot anyway) and used unetbootin to load the latest ubuntu iso.

Under UEFI there is no option for USB and in legacy BIOS selecting the ubuntu pendrive results in no OS found.

Perhaps this pendrive is not bootable? I don't have any others to hand to test but can buy one. I understand the USB option will show when a supported pendrive is plugged in?

UEFI options:
[COLOR=#000000][FONT=Verdana][http://i.imgur.com/R0HjPku.jpg](http://i.imgur.com/R0HjPku.jpg) (link because image is large)[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by waxcan on 2016-01-06
Hey guys, I used a different USB -- lexar from the local shops -- and it worked first go via unetbootin. Guess the eBay USB didn't have the right firmware.

---

### Post by Bucky Ball on 2016-01-06
Good news. Please see the first link in my thread to mark as solved and feel free to post a new thread for any future issues. Good luck. :)

---

