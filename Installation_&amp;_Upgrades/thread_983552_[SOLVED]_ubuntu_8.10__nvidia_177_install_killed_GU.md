---
title: "[SOLVED] ubuntu 8.10 / nvidia 177 install killed GUI"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by FreeThePenguin on 2008-11-15
Hi all,

I have finally decided to give linux another go after having wifi problems in FF.  The new version is great, wifi works fine.  I have a nvidia (appearently fakeraid) raid setup, and i managed to get ubuntu installed on it.  So, i go to boot into the installed os, and i get update notifications, one of which is nvidia display drivers 177.81 so i install that, then reboot.  Now i have no GUI.  after booting i get a login prompt and command line.  I'm quite frustrated at this time as i was eager to start my ubuntu learning experience and i managed to f* it up in about 5mins.  So could someone please help me out here, i'm a complete n00b.

btw, im using x64 and have 2x 8800GTS SLI
I tried 'startx' and it says no screens found.

---

### Post by FreeThePenguin on 2008-11-15
I have tried: 

**sudo dpkg-reconfigure -phigh xserver-xorg**

but it just gives me a warning that its overwriting a config file.  

Is there some way to uninstall the nvidia driver and go back to whatever generic driver it was using?  I dont really care i just want this to work, it came up as an automatic update i didn't realize what i was unleashing.

---

### Post by KK0DJ on 2008-11-15
I too have just installed the same distro, loaded the NVIDIA 177.81 driver, rebooted and get a display error on my monitor that states "Cannot Display This Video Mode - Optimum resolution 1280X1024 60hz"  Trouble is, I cannot find a configuration file to edit these parameters within the shell. Any help is greatly appreciated as well!

---

### Post by KK0DJ on 2008-11-16
Found that reverting back to an earlier NVIDIA driver (93) fixed the problem!

---

### Post by FreeThePenguin on 2008-11-16
> **KK0DJ said:**
> Found that reverting back to an earlier NVIDIA driver (93) fixed the problem!


how do you do this from command-line?

Also, i've tried booting into recovery mode and selecting fix xserver from the menu...  no luck.


ok, i tried something a little different:

**sudo dpkg-redonfigure xserver-xorg**

from a root shell, what i was reading said to select 'nv', i didn't see 'nv' anywhere it asked me a bunch of questions (mostly about keayboard) and when it was done, i did:

[B]sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
[/B]

then i tried:

**starx**

again and here is what i get, it first said something like:

WARNING:  Process is 1 instead of requested 0

I ran startx a second time but this msg did not show again.  At the bottom it says:

> Primary device is not PCI
(EE) No devices detected.

Fatal server error:
no screens found
giving up
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): server error.

occationally it will give be the boot screen (logo & progress bar) but then it just goes to a black screen with cursor.  i can type but it does nothing.

---

### Post by supertdog on 2008-11-16
I'm having the same problem.  Did you ever find a solution?

---

### Post by FreeThePenguin on 2008-11-17
Could this be because i have 2 video cards in SLI and it doesnt know which one to use?  Is there a way to tell it which one to use?

Also the X server message (above) says "Primary device is not PCI"  Well, its PCIe, does that make a difference?

---

### Post by Atro on 2008-11-17
Did you update your Kernel before restarting ?
A friend of mine had the same problem, he chose an earlier kernel version in boot and eveything worked fine

---

### Post by FreeThePenguin on 2008-11-17
> **Atro said:**
> Did you update your Kernel before restarting ?
A friend of mine had the same problem, he chose an earlier kernel version in boot and eveything worked fine

I didn't

---

### Post by eliasz on 2008-11-18
> **FreeThePenguin said:**
> Could this be because i have 2 video cards in SLI and it doesnt know which one to use?  Is there a way to tell it which one to use?

Also the X server message (above) says "Primary device is not PCI"  Well, its PCIe, does that make a difference?

I am having the same problem. I have 7900 SLI PCIe(is there any others?). In 8.04 it worked fine. I have not tried the 93 driver. I will reinstall and give that a shot.

---

### Post by eliasz on 2008-11-18
Hi guys, i found this site. I have not had a chance to test as i am at work, but will give it a shot tonight. [http://lenss.nl/2008/11/ubuntu-810-nvidia-driver-trickery/](http://lenss.nl/2008/11/ubuntu-810-nvidia-driver-trickery/)

---

### Post by oldsoundguy on 2008-11-18
Folks, it is an issue that has yet to be resolved.  Lots of finger pointing and very little progress and the gurus at both Launchpad and NVidia Linux forums ignore all questions concerning the issue.  (could be that they are clueless?) The only people that seem to be working on the problem(s) (and there are quite a few), seem to be at the Envy site.  Go read the blog from the site to get an idea of what they are up against.

Yes.. I am using the 96 driver to be able to, at least,  get default resolution and wide screen display on one of my machines.  NO bells and whistles (forget Compiz)(forget screen rotation). My other two on Ubuntu 8.10 are using the 173 drivers as they are standard ratio LCD's.  For some reason, Linux Mint did not have to be tweaked, but it too, lost the bells and whistles and just is a straight vanilla display.

(to install the older legacy drivers in 8.10, go to synaptic and search for NVidia.  Chose the driver and install, it will remove the other drivers.  Then go to system> administration> hardware drivers> and activate the driver.)

adding this: if the driver you chose will not work with your card or display, it will not show up when you get to hardware drivers using the above path.

---

### Post by FreeThePenguin on 2008-11-18
> **eliasz said:**
> Hi guys, i found this site. I have not had a chance to test as i am at work, but will give it a shot tonight. [http://lenss.nl/2008/11/ubuntu-810-nvidia-driver-trickery/](http://lenss.nl/2008/11/ubuntu-810-nvidia-driver-trickery/)

This worked!  I believe the problem is that it doesnt know which video card to use, and nvidia appearently just leaves importent settings out of the file because its confused.  Here is my /etc/X11/xorg.conf if it helps.

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier 	"Default Layout"
	Screen 		0 "Screen0" 0 0
EndSection

Section "Module"
	Load 		"glx"
EndSection

Section "ServerFlags"
	Option		"Xinerama" "0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Acer"
	ModelName	"Unknown"
	HorizSync	30.0 - 80.0
	VertRefresh	55.0 - 75.0
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo" "True"
EndSection

Section "Device"
	Identifier	"VideoCard0"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporation"
	BoardName	"GeForce 8800 GTS"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"NoLogo" "True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"VideoCard0"
	Monitor		"Monitor0"
	DefaultDepth	24
	Option		"TwinView" "1"
	Option		"TwinViewXineramaInfoOrder" "DFP-0"
	Option		"metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
EndSection

```

---

### Post by Borfo on 2008-12-05
I had the same problem - installed 8.10, everything seemed fine, then installed the 177 drivers for my 8800gt and then X wouldn't start.  I tried all kinds of things, including everything in this thread...  Even went so far as to go out and buy a new power supply thinking that maybe it had something to do with the graphics card being underpowered.

Figured out what it was though, thought I'd post in here to maybe save someone some aggravation.

Turned out it had to do with my motherboard's onboard GPU being enabled, and/or Hybrid SLI being enabled in the BIOS (they were enabled by default for me, I hadn't turned them on on purpose).  I turned both off, and everything worked immediately.

Well, I've got a really awesome power supply now at least.

---

