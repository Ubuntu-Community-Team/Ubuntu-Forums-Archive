---
title: "i want to test without burning a CD"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by madjr on 2009-08-14
no optical drive (cd-rom)

how can i install (or atleast try) alhpa 4 for example

---

### Post by philinux on 2009-08-14
unetbootin or virtualbox

I'd use VB

---

### Post by wayne_cat on 2009-08-14
you could install it from a USB flash drive.

Hint: usb-creator-gtk

---

### Post by fjosh on 2009-08-14
Virtualbox can work with iso's directly off your HDD.

Though it's a poor way to test for hardware compatibility as everything is emulated.

---

### Post by philinux on 2009-08-14
> **fjosh said:**
> Virtualbox can work with iso's directly off your HDD.

Though it's a poor way to test for hardware compatibility as everything is emulated.

Not now, latest version has proper graphics acceleration. It needs to be enabled though. Not available by default.

[http://maketecheasier.com/enable-3d-acceleration-in-virtualbox/2009/05/21](http://maketecheasier.com/enable-3d-acceleration-in-virtualbox/2009/05/21)

---

### Post by phenest on 2009-08-14
> **fjosh said:**
> Virtualbox can work with iso's directly off your HDD.

Though it's a poor way to test for hardware compatibility as everything is emulated.

This is true. But without an optical drive, that leaves a USB stick or network.

---

### Post by phenest on 2009-08-14
> **philinux said:**
> Not now, latest version has proper graphics acceleration.

What about 'other' hardware?

---

### Post by psyke83 on 2009-08-14
> **philinux said:**
> Not now, latest version has proper graphics acceleration. It needs to be enabled though. Not available by default.

[http://maketecheasier.com/enable-3d-acceleration-in-virtualbox/2009/05/21](http://maketecheasier.com/enable-3d-acceleration-in-virtualbox/2009/05/21)

That's great and all, but it still isn't a good idea to test your hardware using virtualization software. Even if the 3D acceleration works, major aspects of the system are emulated - the BIOS, ACPI implementation, sound card, IDE/SATA chipset, etc.

It's entirely possible that a PC would refuse to boot Karmic natively, but would work in VirtualBox. All you're testing is the compatibility of virtualized devices.

---

### Post by philinux on 2009-08-14
> **psyke83 said:**
> That's great and all, but it still isn't a good idea to test your hardware using virtualization software. Even if the 3D acceleration works, major aspects of the system are emulated - the BIOS, ACPI implementation, sound card, IDE/SATA chipset, etc.

It's entirely possible that a PC would refuse to boot Karmic natively, but would work in VirtualBox. All you're testing is the compatibility of virtualized devices.


Agreed but he wants to test without a cdrom. If he has a usb boot enabled pc then that would be way to go.
Or unetbootin.

---

### Post by bacardiandwatermelon on 2009-08-14
usb-creator is the way to go, I never burn cds anymore for my installs...

---

### Post by Seventh Reign on 2009-08-14
The 3D in VB 3.0.4 does NOT work... if I didnt know better I'd think Sun/Oracle was a MS Corporation ... has anyone actually checked their 'about' section?

---

### Post by scaine on 2009-08-14
> **bacardiandwatermelon said:**
> usb-creator is the way to go, I never burn cds anymore for my installs...

Same here - 1Gb key, stick it into an existing Jaunty/Intrepid install and run System/Admin/USB Startup Disk Creator and point it at your downloaded ISO.  If you're using the same key over and over, it's worth doing a "sudo apt-get install gparted" and re-format it beforehand.  Otherwise, very straightforward and reliable.

---

### Post by WishMaster on 2009-08-14
I tried the usb-creator also
After reboot, I can choose "start ubuntu", then a black screen, then the login-sound, but still a black screen. Black screen stays after that...

Acer TravelMater 661 LCi
Pentium-M 1,4 Ghz
	  512 MB RAM (2 x 256)
	  **Intel i855GM chipset** 400 MHz FSB with integrated graphics

---

### Post by jerrylamos on 2009-08-15
> **WishMaster said:**
> I tried the usb-creator also
After reboot, I can choose "start ubuntu", then a black screen, then the login-sound, but still a black screen. Black screen stays after that...

Acer TravelMater 661 LCi
Pentium-M 1,4 Ghz
	  512 MB RAM (2 x 256)
	  **Intel i855GM chipset** 400 MHz FSB with integrated graphics

I don't have an i855.  My i845 will boot to gdm only if I boot in recovery mode, replace "quiet splash" with "single", on the linux line on the grub menu.

On the recovery mode menu root prompt copy in an /etc/X11/xorg.conf.  

nano /etc/X11/xorg.conf and add Driver "vesa" in the next line past "Configured Video Device".

Then exit root prompt and resume boot.....

Jerry

---

### Post by psyke83 on 2009-08-15
> **jerrylamos said:**
> I don't have an i855.  My i845 will boot to gdm only if I boot in recovery mode, replace "quiet splash" with "single", on the linux line on the grub menu.

On the recovery mode menu root prompt copy in an /etc/X11/xorg.conf.  

nano /etc/X11/xorg.conf and add Driver "vesa" in the next line past "Configured Video Device".

Then exit root prompt and resume boot.....

Jerry

The problem is KMS - it's quite buggy on 8xx class Intel chipsets. Boot with the "nomodeset" kernel boot option and the Intel driver will work fine.

P.S. The recovery boot won't work with the Intel driver because it also activates KMS. You can verify this when the terminal expands from 640x480 to 1024x768 (as soon as the drm and i915 kernel modules are loaded).

---

### Post by jerrylamos on 2009-08-16
> **psyke83 said:**
> The problem is KMS - it's quite buggy on 8xx class Intel chipsets. Boot with the "nomodeset" kernel boot option and the Intel driver will work fine.


karmic A4 CD is also buggy on ati radeon Xpress 200, boots to black screen.  I'll have to see if I can ssh into it.  Default is nomodeset on ati.

karmic A4 CD does boot on ati radeon mobility 7500.  No KMS on that one either by default.  radeon.modeset=1 and it does work, but s-l-o-w-l-y.  I've a launchpad bug on that.

I see on the forum someone with nvidia has trouble too.

What video graphics & drivers do work with KMS?  My four test pc's don't like it, either doesn't work or much slower on video graphics benchmark GtkPerf from synaptic.

Jerry

---

### Post by Merk42 on 2009-08-16
I just tried Karmic 9.10 in Virtualbox. I know not an ideal environment, but I just wanted to look at KDE 4.3
I cannot install guest additions though.
I try ```
cd /media/cdrom0
sudo sh ./VBoxLinuxAdditions-x86.run
``` and it just spits and error saying it can't run it.

---

### Post by WishMaster on 2009-08-17
> **psyke83 said:**
> The problem is KMS - it's quite buggy on 8xx class Intel chipsets. Boot with the "nomodeset" kernel boot option and the Intel driver will work fine.
On the boot menu (start Ubuntu without installing, check cd for errors, memory test,...), I pressed F6 and added:

[LIST]
[*]"vga=788" to the boot line --> black screen, nothing happens
[*]"nomodeset" --> I got a (big) Ubuntu loading bar, but then it just stopped. I rebooted after 10min of 'nothingness'
[*]removed "quiet splash" and replaced with "single nomodeset" --> everything went fine, until I got multiple "squashfs errors: unable to read data/page. Followed by "kernel panic: not syncing". Then it just hangs...
[/LIST]
Acer/Intel855: 1  | Ubuntu: 0

---

