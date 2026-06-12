---
title: "Problem Booting Ubuntu"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Red_Scare on 2007-06-16
I recently installed Ubuntu on my computer, but only after a couple difficulties. When I booted directly from the CD I would get a menu of actions such as start or install, mem test etc. and a number of options at the bottom of the screen. Every time I selected start or install (or any of the options if I remember correctly) it would start the linux kernel and then my monitor  would shut of. I turned it back on but it just automatically shut off again as if my computer wasn't even running. I found out that at the main screen when you boot from the CD I burned, the F4 option defaults to VGA. I had to change that option to another resolution in order to get Ubuntu to boot off the CD without my monitor shutting off. 


I got by that problem and installed Ubuntu and did the updates and all. But now when I try and boot Ubuntu from my Dual-Boot menu it starts the linux kernel and my monitor shuts off again, only now there is no option to change from VGA to some other resolution.

I'm not very technically knowledgeable. I thought it might be something I have set incorrectly in my Bios but I looked at my mobo instruction booklet for the Bios set up but I couldn't find anything that seemed to be the problem.

Any help would be greatly appreciated.

---

### Post by cuby on 2007-06-16
Hi!
This is hapening because your monitor doesn't support the configured resolution...
I think ubuntu didn't recognise the monitor and is trying to feed an  unsupported resolution.
Run ubuntu in text mode and edit /etc/X11/xorg.conf:

sudo pico /etc/X11/xorg.conf

help here:
[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html)
here is a sample of my file, the part you need to edit is this one:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option         "DPMS"
	VendorName "Monitor Vendor"
	ModelName "Samsung SyncMaster 917MB/950MB/957MB/CD197D(P)"
	HorizSync 30.0 - 96.0
	VertRefresh 50.0 - 160.0
EndSection

search the net for xorg.conf and the model of your monitor, change the config and type gdm to start the graphic interface.

---

