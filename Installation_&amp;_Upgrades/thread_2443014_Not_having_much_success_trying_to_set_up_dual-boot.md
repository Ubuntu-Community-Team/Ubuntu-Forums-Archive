---
title: "Not having much success trying to set up dual-boot with Windows 10"
date: 2020-05-10
forum: Installation &amp; Upgrades
---

### Post by mercury-1967 on 2020-05-10
I'm trying to install Ubuntu alongside Windows 10 on my laptop per [these instructions]("https://www.tecmint.com/install-ubuntu-alongside-with-windows-dual-boot/") and I'm not having much luck.

I have a partition set up, the ISO on a USB and I'm able to boot with the USB and get to the Ubuntu desktop, but that's as far as I can get.

I click the desktop shortcut to start the installation, enter my WIFI password, leave "normal installation" selected and click Continue. (somewhere in there is a language selection and I don't recall the exact order of those steps, but you get the idea).

But when I click Continue, I get the spinning mouse icon for a while, then after about an hour that stops spinning and the system freezes and I end up having to hold the power button down to force a shutdown.

I tried that several times with the same results. I then just booted to the desktop, entered my WIFI password (which isn't being saved for some reason), but aside from opening a browser, pretty much **anything** that I do - start a program, try to get in to settings, etc, the system freezes up and I have to force a shutdown.

What should I do at this point?

---

### Post by yancek on 2020-05-10
Some steps seem to be missing in the link you posted so I would suggest that you first read through the official Ubuntu Documentation on the subject at the link below.  After using Disk Management in window you should reboot windows to make sure it did not create any problems if you have not done that.  Note the comments at the link below regarding fastboot/hibernation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

>  I then just booted to the desktop, entered my WIFI password (which isn't being saved for some reason) 

The reason is that it is a 'live' system which is read-only by design and no changes are saved on reboot.  If you've previously been using windows you would not be familiar with this as there are no 'live' windows systems.

---

### Post by mercury-1967 on 2020-05-10
[SIZE=2][FONT=arial]I'm sorry, I failed to mention that I was also referring to [this guide at itsfoss.com]("https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/"). Per that site's instructions, I did disable fast startup and secure boot and I did reboot the system after changing the partitions.

I started going through the official documentation that you linked but when I got to step [4.3, Preparing Files for USB Memory Stick Booting]("https://help.ubuntu.com/lts/installation-guide/amd64/ch04s03.html"), the first sentence stopped me and made me wonder if I'm reading the right instructions. The sentence starts out, "To prepare the USB stick, you will need a system where GNU/Linux is already running". Obviously I have a Windows system, so I don't have access to a system that is already running GNU/Linux.

Did I get myself to the wrong directions?[/FONT][/SIZE]

---

### Post by CelticWarrior on 2020-05-10
There are many ways/tools for making the installation media in Windows. Rufus seems to be quite popular nowadays but depending on the settings it may not boot in UEFI mode so make sure it is set to UEFI/GPT before "burning". Or use Balena Etcher that makes it work in BIOS or UEFI because it's a bit-by-bit copy of the ISO.

---

### Post by mercury-1967 on 2020-05-10
I went through and checked all of the pre-install steps:

I made sure that Secure Boot and Fast Startup were disabled.

I also went into the BIOS and checked the UEFI settings, which are listed as follows:

[LIST]
[*]UEFI/Legacy Boot - Both
[*]UEFI/Legacy Boot Priority - UEFI First
[*]CSM Support - Yes
[/LIST]

I have a 75GB unallocated partition showing in Disk Management. That's the only unallocated partition - there are two recovery partitions and the C: partition.

I reformatted the USB to NTFS file system.

I used Rufus this time to burn the ISO to the USB. Here's a screenshot of those settings:
[ATTACH=CONFIG]285811[/ATTACH]

When I tried installing this time, I got a bit further than my first experience described in my original post. I got to the step that checks the drive for partitions, and oddly, it didn't detect the Windows partition. I did some Googling and it seems a possible reason could have something to do with UEFI, but as far as I can tell that's all set up correctly, but correct me if you see something wrong.

I'm going to re-try the install and see what happens.

---

### Post by CelticWarrior on 2020-05-10
As I explicitly said before: WRONG settings. You need UEFI/GPT.
And it's usually better to disable Legacy/CSM -> This assures the USB is being booted in the correct UEFI mode.

---

### Post by oldfred on 2020-05-10
What brand/model system? What video card/chip?
Are drives set in UEFI to use AHCI, not RAID nor Intel RST?
Searching for partitions can take a bit if you have lots of partitions (I do), but it can go forever is Windows fast start up is on, drives are not AHCI, or some other reason partitions cannot be seen by installer. 
Installer seems a bit more particular than gparted.

---

### Post by mercury-1967 on 2020-05-10
Celtic,

You're right - you did mention the UEFI setting. Sorry about that.
I'm currently re-formatting and will flash the ISO with balenaEtcher. I'll also disable Legacy & CSM.
_______________________

oldfred,

I'm doing this on a Lenovo ThinkPad with an nVidia GeForce GTX 1050 Ti.
I haven't noticed anything mentioning AHCI, RAID or Intel RST while in the BIOS, but I'll double-check.

---

### Post by oldfred on 2020-05-10
With nVidia you will need nomodeset boot parameter.
New versions of Ubuntu will now give you the option to install the nVidia driver as part of install. Otherwise you need nomodeset to boot after install or until you install nVidia driver. Do not install from nVidia directly.

UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mercury-1967 on 2020-05-10
Thanks for all of the info, Fred!

Fortunately, my particular laptop (ThinkPad X1 Extreme) isn't listed in the firmware update.

Noob question incoming: what's "grub" and where/when will I come across it?

---

### Post by oldfred on 2020-05-10
Grub is just the name of the boot loader software. 
It is separately developed, but many distributions use it.
Full manual, but you can read introduction if you want more info:
[https://www.gnu.org/software/grub/manual/grub/grub.pdf](https://www.gnu.org/software/grub/manual/grub/grub.pdf)

See also link in my signature and at bottom is list of Acronyms and more info on each.
Link from that list:
[https://wiki.archlinux.org/index.php/GRUB](https://wiki.archlinux.org/index.php/GRUB)

---

