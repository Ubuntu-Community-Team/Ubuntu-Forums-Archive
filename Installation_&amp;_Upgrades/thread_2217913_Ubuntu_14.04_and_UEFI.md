---
title: "Ubuntu 14.04 and UEFI"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by dunkuk_gelay on 2014-04-18
Laptop Inspiron 5437
Windows 8.1
Ubuntu 14.04 x32

Hi guys, before I make things worst I think it's better if I head here for help. So I use LiLi to make Ubuntu USB since I prefer install from USB. But with UEFI on, my laptop unable to boot into the USB thus I disable UEFI.

So I choose like I always do, install grub at dev/sda/. After that, I received one warning related to the bootlader installation dir, something like partition for bootloader. I ignore since I never get this kind of issue with previous release, installation completed.

Still with legacy mode boot, I restart my laptop, no grub list. The machine instantly boot into Ubuntu. So, I turn on UEFI and the machine instantly boot into Windows 8.1. Fast startup, fast boot, IRST disabled but no success. 

I wondering if I can fix this without re-install or do I need to install Ubuntu in UEFI compatible mode?

---

### Post by oldfred on 2014-04-19
If you installed with the 32 bit version, it is BIOS only. 
You need the 64 bit version which is both UEFI and BIOS. How you boot installer is then how it installs.

With your 32 bit version you have to be in BIOS/CSM/Legacy mode in UEFI/BIOS to boot Ubuntu. If in UEFI mode then only Windows will boot.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Be sure to click on link in my signature. 
Make full backup of Windows and a Windows repair flash drive.
Only use manual install or something Else, as many are having issues with a second install where the default says to overwrite Ubuntu (does not mention Windows) and erases entire drive. Not sure if installer or something in Windows makes it hidden to installer on reinstall.

---

### Post by dunkuk_gelay on 2014-04-19
> **oldfred said:**
> If you installed with the 32 bit version, it is BIOS only. 
You need the 64 bit version which is both UEFI and BIOS. How you boot installer is then how it installs.

With your 32 bit version you have to be in BIOS/CSM/Legacy mode in UEFI/BIOS to boot Ubuntu. If in UEFI mode then only Windows will boot.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Be sure to click on link in my signature. 
Make full backup of Windows and a Windows repair flash drive.
Only use manual install or something Else, as many are having issues with a second install where the default says to overwrite Ubuntu (does not mention Windows) and erases entire drive. Not sure if installer or something in Windows makes it hidden to installer on reinstall.

Thanks mate. I guess need to download the x64 since I expect no more this kind of issue with x32 14.04.

---

### Post by dunkuk_gelay on 2014-04-19
Hey, it works. Now I post this from my Ubuntu. Too bad still not familiar with Unity. :( I prefer Gnome 2 era. Quite unfamiliar with Gnome 3 for my Fedora machine too. Thanks again mate... Should have try x64 first before I create a thread. Phew....

---

### Post by oldfred on 2014-04-19
Not a fan of Unity either, so I install fallback/flashback which is very similar to the old gnome2 menus.

Some of this is 12.04 with fallback, but 14.04 with flashback is the same.
 [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)
You can reset gnome-panel settings to default:
dconf reset -f /org/gnome/gnome-panel/
[http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04](http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04)

---

