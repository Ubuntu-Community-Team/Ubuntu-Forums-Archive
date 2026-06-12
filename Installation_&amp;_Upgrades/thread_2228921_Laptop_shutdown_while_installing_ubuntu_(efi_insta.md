---
title: "Laptop shutdown while installing ubuntu (efi install)"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by shahbazkhan425 on 2014-06-10
[COLOR=#333333]I have lenovo G505s laptop (1TB HDD/8 GB RAM/2 GB graphics/ AMD-A10 processor). I want to install ubuntu alongside win8 (EFI)[/COLOR]

[COLOR=#333333]I created live usb with RUFUS.[/COLOR]
I got the grub menu and booted into live mode. booting completed.  i got the desktop. after few seconds with no warning or message laptop just power off itself.

[COLOR=#333333][/COLOR]I have tried with ubuntu-studio too and same thing happened.  

I dont know how to find out what is causing this problem.

Please help me out here

---

### Post by oldfred on 2014-06-10
While different model this user says his needed a UEFI/BIOS update as suspend to RAM is broken.
Vendors often have similar UEFI configurations across models, so it could be common?

 Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

Others who seemed to get it to work, various model Lenovo

 Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)
Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)

---

### Post by shahbazkhan425 on 2014-06-10
thanks for all the links, but my problem is different,  
in all the links the problem is of grub menu, and other fixes to get it ubuntu working alongside windows.

I can successfully get the system booted into live node or start the installation but after sometime (1-2 minute)
laptop just power off (like u have removed its battery)

i dont even know where to look to find reason behind this.

---

### Post by oldfred on 2014-06-10
Some systems have overheating issues?
If dual video can you set to only use Intel video?

I would go into live mode and run top from terminal to see if something is running in the background that causes issues or processor to 100%.

---

### Post by shahbazkhan425 on 2014-06-10
i dont have intel graphics. i hava AMD's radeon 8650

i booted into live mode with nomodeset option and ran top. no process was consuming CPUs 100%.
i have touched the base of laptop, it wasnt that hot for system to shutdown inorder to protect hardware

is it problem with hardware or some configuration options of ubuntu coz win8 is working fine?

---

### Post by oldfred on 2014-06-10
I do not know AMD, have you installed its proprietary driver?

 AMD Radeon R9 290 On Ubuntu 14.04 With Catalyst Can Beat Windows 8.1
 the open-source AMD Hawaii support remains broken,
[http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1](http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1)
[http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1)

---

### Post by shahbazkhan425 on 2014-06-10
no i havent installed proprietary driver bcoz
1. i havent installed ubuntu bcoz of shutdown problem, i ran it in live mode
2. it takes time to install amd proprietary driver on ubuntu which i cant get bcoz of this damn problem.

why windows doesnot give this problem?

---

### Post by blair-antcliffe on 2014-06-10
I've had a similar problem with a custom build, and have been looking around at it today. This thread [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1309578") gave me some information. I can't test it, as I'm at work, but it seems as though there is a problem with the kernel (linux 3.13) which causes instabilities with A-series APUs.

The workaround seems to be that while ubuntu is loading, hit <shift> to go into the options. In boot options, tell it to pass to the kernel the command "radeon.dpm=0". After install, make sure to go and edit the grub itself to permanently pass this option. Alternatively, install a newer kernel (3.14 or 3.15) after installing ubuntu.

---

### Post by shahbazkhan425 on 2014-06-10
in bios settings, i changed the graphics option from 'switchable' to UMA. then tried installing ubuntu.
SURPRISINGLY no power off and installation completed. :D
the grub menu showed the entry of ubuntu and windows 8 and both options working.

THANK you    oldfred and blair-antcliffe.

---

