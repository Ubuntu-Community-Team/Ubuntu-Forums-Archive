---
title: "Firefox and Facebook"
date: 2009-01-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by keep-on-smiling on 2009-01-04
Hi

A small issue, but wondering if this is just me...

I installed the 25-12-08 version of Jaunty, did all the updates and then started looking around the web, doing the bookmarks etc and tried Facebook. First thing I noticed is that the big blue strip on the login page has gone - that confused me enough to go get the url from the XP partition (and to check the site in Firefox in XP). Any rate, I then logged in and found the blue strip behind the navigational links at the top of each page only showed up on mouse-over.

Does anyone else have this issue ?

Cheers

---

### Post by keep-on-smiling on 2009-01-04
Hi

Just booted back into XP and the two systems run the same version of Firefox (3.05) - strange how they behave differently

cheers

---

### Post by samjh on 2009-01-11
Yup, I have the same issue.  Jaunty + Firefox 3.0.5.

It's not just Facebook.  Some websites show artifacts (parts of the topmost window).

I've attached screenshots of the Facebook mis-render (the rectangular section at the top of the page should be much darker), and the other mis-rendering phenomenon.

[[IMG]http://img262.imageshack.us/img262/4468/screenshotmu0.th.png[/IMG]](http://img262.imageshack.us/my.php?image=screenshotmu0.png)

[[IMG]http://img238.imageshack.us/img238/4198/screenshot1at7.th.jpg[/IMG]](http://img238.imageshack.us/my.php?image=screenshot1at7.jpg)

I'm not sure whether this is actually a Firefox problem, or a Gecko problem, or a problem with Gnome/GTK/Cairo/Xorg/etc.

LOL, I just tried to open one of my screenshots on Imageshack, and it doesn't show!

[[IMG]http://img142.imageshack.us/img142/5371/screenshot2ky3.th.png[/IMG]](http://img142.imageshack.us/my.php?image=screenshot2ky3.png)

---

### Post by asac on 2009-01-11
Are you all using AccelMethod Xaa? Or is this an issue with EXA too? (check your Xorg.0.log)

---

### Post by asac on 2009-01-11
If you are using Xaa, you probably can work around by disabling offscreen pixmaps in your xorg.conf devices section:

Option "XAANoOffscreenPixmaps" "true"

Let us know.

---

### Post by keep-on-smiling on 2009-01-11
hi

this is what appears to be the relevant bit of the log:

----------------------------------
(**) NV(0): Display dimensions: (380, 300) mm
(**) NV(0): DPI set to (85, 86)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
------------------------------------

so am going to try your suggestion :) will let you know

thanks

---

### Post by keep-on-smiling on 2009-01-11
Hi Asac

Yep that suggestion fixed the issue:

sudo nano -w /etc/X11/xorg.conf

then in the devices section paste: 
Option "XAANoOffscreenPixmaps" "true"

save and close. 

I rebooted to check if this would affect the system in any way.
No probs. And Facebook now looks exactly like it does in XP :)

Many thanks !

---

### Post by keep-on-smiling on 2009-01-11
for extra clarity, here is the updated xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Option          "XAANoOffscreenPixmaps"         "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

cheers !!

---

### Post by keep-on-smiling on 2009-01-11
For what it is worth, I am running an nVidia FX5500, but with the standard nv driver - don't want to go fiddling with adding a "blob" until things are closer to beta. Having said that the system is mostly stable :)

cheers

---

### Post by samjh on 2009-01-11
> **asac said:**
> If you are using Xaa, you probably can work around by disabling offscreen pixmaps in your xorg.conf devices section:

Option "XAANoOffscreenPixmaps" "true"

Let us know.

That worked.  Thank you. :)

Do you know if this is a bug, or is it an intentional thing?  If it's a bug, is there a report on Launchpad?

---

### Post by keep-on-smiling on 2009-01-14
hi

i would not say for sure, but would consider this a bug - surely the devs did not intentionally cause issues with facebook ?

hopefully there will be a bug fix for this - ideally the xorg.conf is not supposed to be fiddled with these days in ubuntu, barring workarounds like this.

cheers

---

