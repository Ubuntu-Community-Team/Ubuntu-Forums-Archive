---
title: "Blank screen during USB install"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by M@s on 2011-12-08
I'm trying to install Ubuntu 11.10 x64 from an USB stick on an Asus U36SD. It boots up and I get into the installer menu, and I get to choose between trying or installing Ubuntu, or check disk for errors. No matter which option I choose, it follows by a complete blank black screen and nothing more.

I've tested with both the LiveCD and the Alternate installer, as well as Ubuntu Studio 11.10 x64, and the problem occurs on all of them. Even tried 2 other USB sticks with the same result.

This has been working before, I installed 11.04 some time ago. Anyone knows what's wrong?

---

### Post by MAFoElffen on 2011-12-08
> **M@s said:**
> I'm trying to install Ubuntu 11.10 x64 from an USB stick on an Asus U36SD. It boots up and I get into the installer menu, and I get to choose between trying or installing Ubuntu, or check disk for errors. No matter which option I choose, it follows by a complete blank black screen and nothing more.

I've tested with both the LiveCD and the Alternate installer, as well as Ubuntu Studio 11.10 x64, and the problem occurs on all of them. Even tried 2 other USB sticks with the same result.

This has been working before, I installed 11.04 some time ago. Anyone knows what's wrong?
You hve nvidia graphics... Use "nomodeset" as a kernel boot option:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]

After your install and have to reboot, then use this method to use "nomodeset" again... Then install your driver from the Additional Drivers Applet.
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

Tell me how it goes...

---

### Post by M@s on 2011-12-09
> **MAFoElffen said:**
> You hve nvidia graphics... Use "nomodeset" as a kernel boot option:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]
Thanks! But I can't get it working. I never get into the Casper/Isolinux menu, the first screen that boots up is one titled "GNU GRUB version 1.99-12ubuntu5". I can edit the boot options by pressing 'e' and this is what it looks like with the nomodeset option:


```
setparams 'Try Ubuntu without installing'
set gfxpayload=keep
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quitet splash -- nomodeset
initrd /casper/initrd.lz
```
I boot it up and still nothing more than a blank screen.

---

### Post by MAFoElffen on 2011-12-09
> **M@s said:**
> Thanks! But I can't get it working. I never get into the Casper/Isolinux menu, the first screen that boots up is one titled "GNU GRUB version 1.99-12ubuntu5". I can edit the boot options by pressing 'e' and this is what it looks like with the nomodeset option:


```
setparams 'Try Ubuntu without installing'
set gfxpayload=keep
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quitet splash -- nomodeset
initrd /casper/initrd.lz
```I boot it up and still nothing more than a blank screen.
So how did you create your Live USB image and what brand USB stick?

---

### Post by M@s on 2011-12-10
> **MAFoElffen said:**
> So how did you create your Live USB image and what brand USB stick?I've tested both the Startup Disk Creator and UNetBootin. My USB stick is a Deltaco Nano 8GB, but I've tested with 2 other sticks as well that have been working before and the problem persists.

---

### Post by housseinireza on 2012-03-07
Hi,
the same problem appears to me, also with ubuntu 11.10 64bit on an asus pc. After selecting one of the menu entries from grub menu, nothing happens and a blank screen appears. The ubs works correctly I already installed ubuntu 11.04 on an other pc. Has anyone figured out the cause?

Best wishes,
Reza

edit: after pressing esc at startup and selecting the usb drive, a very short instance an error shows up before entering the grub menu:
error: prefix is not set
is this related to my boot options?

---

### Post by tuanita on 2012-03-08
> **M@s said:**
> I'm trying to install Ubuntu 11.10 x64 from an USB stick on an Asus U36SD. It boots up and I get into the installer menu, and I get to choose between trying or installing Ubuntu, or check disk for errors. No matter which option I choose, it follows by a complete blank black screen and nothing more.

I've tested with both the LiveCD and the Alternate installer, as well as Ubuntu Studio 11.10 x64, and the problem occurs on all of them. Even tried 2 other USB sticks with the same result.

This has been working before, I installed 11.04 some time ago. Anyone knows what's wrong?

Yes men, i know what's wrong, Ubuntu doesn't support some graphic brands like nVidia, Radeon etc. I just got installed for myself the latest beta version of 12.04 and it works, no black screen at all. Try,nothing to lose!

---

