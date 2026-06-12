---
title: "problem with RV710 chip (HD 4550) and high resolution on Dell U2711 solved in 10.10"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by kmart on 2010-10-13
Hi,

Just to inform you that the problem that I asked around about in the now closed thread

[http://ubuntuforums.org/showthread.php?t=1442695](http://ubuntuforums.org/showthread.php?t=1442695)

for about half a year ago, is not present in 10.10. That is I can now use the Dell U2711 monitor at its full resolution, using a Radeon HD 4550 (RV710) card, with acceleration and without the image beeing distorted, using the open xorg radeon driver.

This is great, no more fglrx!

kmm

---

### Post by fpalmer_35 on 2010-10-18
Hi,

I also have a Radeon HD 4550 (RV710) card.
How did you solved the problem ?

With the ati driver ? (witch version 10.9 ?)

Thanks
Franck

---

### Post by kmart on 2010-10-23
> **fpalmer_35 said:**
> 
How did you solved the problem ?

With the ati driver ? (witch version 10.9 ?)


Hi,

Did nothing really. Just installed Maverick from scratch and the card worked right away. No 'xorg.conf' file or anything.

It is really the radeon driver, as loaded by the 'ati' (wrapper) driver, from the 'xserver-xorg-video-radeon' deb package. 'apt-cache show' reports 6.13.1 as its version number.

br,
kmm

---

### Post by fpalmer_35 on 2010-10-26
> **kmart said:**
> Hi,

Did nothing really. Just installed Maverick from scratch and the card worked right away. No 'xorg.conf' file or anything.

It is really the radeon driver, as loaded by the 'ati' (wrapper) driver, from the 'xserver-xorg-video-radeon' deb package. 'apt-cache show' reports 6.13.1 as its version number.

br,
kmm

Thanks for that.

My install is not a fresh one, it's an upgrade from 10.4 to 10.10.
The screen definition is good, but I do not have 3D acceleration.

I also have this pkg installed but also fglrx-amdcccle, fglrx, radeontool.
but fglrxinfo  report me this error :

[HTML]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14[/HTML]

The device part of my xorg.conf is :

[HTML]Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "radeon"
	BusID       "PCI:5:0:0"
	Option	    "DRI"
        Option   "AccelMethod" "EXA"
EndSection[/HTML]

What is yours ?

---

### Post by kmart on 2010-10-28
Hi,

> **fpalmer_35 said:**
> I also have this pkg installed but also fglrx-amdcccle, fglrx, radeontool.
but fglrxinfo  report me this error :

I don't have the fglrx tools but the Mesa ones (glx*, from the 'mesa-util' package). The 'glxinfo' command reports a lot (250 lines with output!) but do says that "direct rendering" is enabled and, further down in the list, that the GLX version is 1.4 and all the 'GLX_*' extensions suppoted and so on.

And 'compiz' works! Am using the 'normal' setting for 'visual effects' for the desktop.

> **fpalmer_35 said:**
> 
The device part of my xorg.conf is :

No 'xorg.conf' file here. Seems to work fine without it.

Could it be that you are experiencing some kind of conflict between the fglrx driver and the radeon driver and/or tools? Maybe a fresh install would help (a bit drastic perhaps)? Or perhaps see if it goes better with the 'fglrx*' packages and the 'xorg.conf' file removed? (Such experimentation could cause its own problems though...)

br,
kmm

---

