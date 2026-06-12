---
title: "Usb install"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by jmdlcar on 2010-09-15
Will I have any programs with Ubuntu is going from my computer to my laptop when it save the setting from the first computer then boot from the other?

---

### Post by oldfred on 2010-09-16
Not quite clear on what your are doing. Are you doing a full new install on you laptop and want your settings or programs from the desktop.

All the parts of a backup may be used except some settings from/etc as that may be unique to your hardware. You need to review those.

I backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script I wrote to generate the backup
List of sources:
5. sudo cp /etc/apt/sources.list ~/sources.list.backup
Installed applications list (to make it easy to reinstall everything)#
dpkg --get-selections | grep -v deinstall > ubuntu-files
or
6. dpkg --get-selections > ubuntu-files

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

### Post by efflandt on 2010-09-16
It depends if you are asking about live/install iso on bootable USB like from Startup Disk creator or a regular full install to USB.

Of course if you do a regular full install to USB (including grub in the mbr of the usb using the Advanced button during install) then anything you install or save while running from that drive is preserved.  The only thing that might give you errors is if you use certain proprietary drivers (like for video) and do not have such hardware on the other PC, but that would typically just be an error that a module in xorg.conf cannot load and you might not have accelerated video, although, it would probably still work.  Although, that is not usually a problem for other hardware like wireless unless the computers require different mutually exclusive proprietary drivers (like Broadcom STA for one and Broadcom B43 for another).

For example 64-bit 10.04 installed to 160 GB USB boots fine from 4 different computers (2 desktops, 2 laptops). If Broadcom STA is activated, it is used if needed or ignored on others without Broadcom, and wireless works either way.  However, I had to use **partman/alignment=cylinder** boot parameter during install for it to boot on an old Athlon64 from 2004 with Asus mobo, and **radeon.modeset=0** to not use kms on older ATI Radeon w/default video drivers.  Or if I activate nVidia proprietary drivers for new desktop, I get errors, but it still works for ATI or Intel on other PC's, but without GL that it would use with all default video drivers.  So you may want to stick with default video drivers if possible when using it for multiple PC's with different video.  If necessary you could use bash scripts with xrandr commands for nonstandard resolutions on non-digital monitors, but I only have to do that for external VGA HDTV on laptops because my desktops use DVI.

If it is a live/install iso on USB instead, you would need persistent data (casper-rw) in order to save settings, added programs, or files saved while running from that (other than files save to any other available disk space on other filesystem on the USB_.  And if you install from a live system with persistent data it will use certain settings from there as defaults for things like time zone and network (wireless) settings.  When booted from another Linux system, you can get at persistent data by loop mounting casper-rw file (which is an ext2 filesystem).

---

### Post by jmdlcar on 2010-09-16
What I did is took the live cd and install it on a portable 320gb usb drive. And want to use it on 2 computer.

As cheap as portable 320gb usb drive are I to buy 2 and use 1 for each but I will try it first to see if will work but I haven't bought the laptop yet.

---

### Post by C.S.Cameron on 2010-09-16
Your USB drive should work on any computer that boots to USB as lon as you don't install any restricted drivers.

---

### Post by ujjainnaga on 2010-09-16
i am not able to modify the content of my pen drive.
i mean cant delete any content of pendrive.
pls help me out.

---

### Post by C.S.Cameron on 2010-09-16
> **ujjainnaga said:**
> i am not able to modify the content of my pen drive.
i mean cant delete any content of pendrive.
pls help me out.

Check your pendrive manufacturer's web page, they may offer an utility to fix it.

---

### Post by ujjainnaga on 2010-09-17
> **C.S.Cameron said:**
> Check your pendrive manufacturer's web page, they may offer an utility to fix it.
it is not related with any particular pen drive .

after installing E1550 huwei 3g modem the problem started.
i cant delete or modify the content of any pen drive.
pls help me out.
these are the steps i have followed:

gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules

SUBSYSTEM=="usb",SYSFS{idProduct}=="1446",SYSFS{idVendor}=="12d1",RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

---

