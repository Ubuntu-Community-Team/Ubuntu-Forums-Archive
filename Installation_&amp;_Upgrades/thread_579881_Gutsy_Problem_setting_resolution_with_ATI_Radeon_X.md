---
title: "Gutsy: Problem setting resolution with ATI Radeon X1950 / Samsung 22&quot; monitor!"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by tnaseem on 2007-10-18
I've been through a number of threads with similar problems, but am unable to solve this!

I have been using Feisty Fawn with no problems with my ATI X1950 gfx card and Samsung 226BW monitor at the native resolution, together with the restricted drivers, etc. All worked beautifully.

I've now upgraded to Gutsy Gibbon and have come across problems (FYI, I've now just tried a fresh install with the same results).

All installs fine. Initially, I'm presented with a 1024x768 resolution screen. I then enable the restricted driver and reboot.

The next time it boots, I'm in 640x480. At the login prompt it tells me that I'm running in low resolution and allows me to configure the screen. I select the correct monitor from the list (Samsung 226BW (Digital) as I'm connected via DVI. I then select the native 1680x1050 (60Hz) resolution. However, this gives me a garbled screen (as if the refresh rate is set wrong).

I've tried selecting different drivers from the drivers list (radeon / vesa), but I still get this garbled screen. I've also tried it with and without the restricted driver, but can't seem to get anywhere with it!

Feisty Fawn had no such problems! I merely enabled the restricted drivers and resolution and it worked flawlessly.

I initially thought it was something to do with upgrading, so I wiped everything and reinstalled from scratch. Same result! I've even fiddled with the xorg.conf file as suggested elswhere here, but nothing seems to fix it.

Any help would be appreciated! If you need further info, please let me know!

Cheers,
Tarique.

---

### Post by mattpker on 2007-10-18
Have you tried using the actuall ATI Linux drivers? Also the xorg.conf is probly were the issue lies. If you can copy the Monitor and Video Card parts and paste them here.

---

### Post by tnaseem on 2007-10-18
Hi,

Thanks for your reply.

I'm now logged in and selected the Samsung SyncMaster 226BW monitor. I have 1680x1050 selected, but the screen remains at 800x600. The restricted driver is also installed and active according to the 'Restricted Drivers Manager'. The relevant parts of the xorg.conf are as follows.

```

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 226BW (Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1600x1024@60"	"1680x1050@60"	"1440x900@60"	"1920x1200@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection


```

```

Section "device" #  
	Identifier	"device1"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:1:0:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection

```

One thing to note: I also selected the 'Radeon' driver in 'Screens and Graphics' config. However, this just gave me a black screen for a few seconds before dropping me into a console screen, and then back to the login prompt! So I left it as the default VESA, assuming the resirticted ATI driver would take care of it. Obviously, it hasn't! Even though it says it's enabled, I'm sure it isn't!

In fact, as I'm typing this, I've just run 'Screens and Graphics' again, and it doesn't list my monitor any more or the resolution I set. It currently says 'Plug and Play' monitor at 800x600. So even though I did set it, it doesn't want to remember the setting; nor did it actually change anything when I did set it!

I'm so confused. This was so much easier under Feisty!

By the way, I did also try the 'sudo dpkg-reconfigure xserver-xorg' method, but that didn't work either. Although, I only half knew what to answer to each question :)

Any help much appreciated!

Cheers,
Taz

---

### Post by SculptusPoe on 2007-10-19
There needs to be some way to force the settings to save. A 1024-768 generic using the ATi Radion drivers would work fine for me. The setting seems to be there but when I restart it gos back to 800-600 and takes away the higher resolution option. It worked fine in feisty. I suppose it's a problem with the monitor auto detect. Is there some way of turning this off?

---

### Post by SculptusPoe on 2007-10-19
I think I found the fix.

In the X11 folder, edit Xsession.options and comment out allow-failsafe

The failsafe apparently jumps to an alternate X11.conf file at the first sign of a problem if failsafe is set. This wouldn't be so bad, but it does this even if it would have worked. 

The only problem is that i suppose there is a possibility you could run into a problem if you have a setting that really wouldn't work. You may have to end up editing your x11 conf by hand from safemode.

```
# $Id: Xsession.options 189 2005-06-11 00:04:27Z branden $
#
# configuration options for /etc/X11/Xsession
# See Xsession.options(5) for an explanation of the available options.
#allow-failsafe
allow-user-resources
allow-user-xsession
use-ssh-agent
use-session-dbus
```

---

### Post by tnaseem on 2007-10-23
@SculptusPoe: Thanks for the tip. Unfortunately, that doesn't work in my case. If I had hair, I'd be pulling i out by now!

---

### Post by Maulwuff on 2007-11-16
if you don't mind to work with nano or something else, try to disable the failsafe xserver, to see, why the normal xserver does not start.

in: /etc/gdm/gdm.conf edit the FailSafe setting:
Original:
FailsafeXServer=/etc/gdm/failsafeXServer

I changed it to
FailsafeXServer=
now I can see the error message of xserver again. (In my case I had a " too much...)

---

