---
title: "Installer crashes - low disk space"
date: 2016-08-11
forum: Installation &amp; Upgrades
---

### Post by fwhitaker on 2016-08-11
Hello! I am totally at a loss here. I am trying to install Ubuntu on a desktop (I would settle for literally any version at this point), and it never completes the process. Here is what happens:


[LIST=1]
[*]I create a bootable flash drive or dvd.
[*]I successfully boot from said object. The Ubuntu installer initially runs.
[*]It prompts me for installation type, and I select 'clear disk and install.'
[*]It prompts me for a bunch of other things: region, login, etc...
[*]It then gets to the screen where it claims it is installing Ubuntu, and shows a slideshow of all the great things Ubuntu can do if it actually runs
[*]It gets towards the end of installing, then crashes
[*]The computer says that there is no disc space remaining.
[*]If I am using the "try Ubuntu before installing" option, I then take this opportunity to go to the menu and tell it to shut down. I am then greeted by infinite scrolling text.
[/LIST]

That is the gist of it, but I have tried many things now.
Sometimes, the installer does not even get that far. Most recently, it crashed on the "for best results, please ensure..." screen. However, it almost always cites low disc space in addition to the actual error popup, and the error popup usually states more information can be found in var/log/syslog. This file is absolutely MASSIVE, usually about 4GB. I assume that this file filling up causes the disk storage problem, which the Disk Usage Analyzer suggests. The / folder is 13.5 gb, and its usage is 100%.

This computer is an ASUS Realtek RTL8821AE. The monitor is an HP 22cwa. The computer has UEFI in addition to BIOS. Some things I have tried with the BIOS/UEFI options:
I tried enabling legacy mode for all boots (turning UEFI off) and that just got me to the infinite scrolling text immediately after showing the Ubuntu logo.
Fast boot is off.
When it first boots, and gives me the option to just install, or run Ubuntu, I have tried running the 'check disc for defects' option, and it said there were no problems.
Secure boot is disabled by removing the PK: [http://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility](http://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility)
I did go through this article, and am pretty sure I am following everything: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I did not run the boot repair because Ubuntu is not even installing

I have tried booting from:
USB stick - both 14 LTS and 16 LTS
DVD - 14 LTS

I have tried turning the wifi off (in the "try Ubuntu" version of the boot)
no dice on anything

I now basically have a bricked computer, because Ubuntu was kind enough to delete Windows before crashing. Irony is a bitch, and a beautiful one.
Let me know if there is anything else I can do.

---

### Post by fwhitaker on 2016-08-12
I also tried booting Fedora - this also fails, and gives me the exact same speedy scrolling text. It seems to fail somewhere around 'starting gnome display manager'...
I really could use some help with this, I now have a bricked new computer.

---

