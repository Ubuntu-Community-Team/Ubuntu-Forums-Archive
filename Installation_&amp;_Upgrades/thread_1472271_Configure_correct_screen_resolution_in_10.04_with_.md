---
title: "Configure correct screen resolution in 10.04 with VIA chipset VN800"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by coady on 2010-05-04
Hi,

Finally decided to upgrade to Lucid, after not wanting the hassle of having to configure my laptop with its hideous VIA chipset. Anyway, I did a clean installation of 10.04 and it booted straight into a functioning desktop. Pretty good (compared with past encounters). :D The only issue is the screen res was incorrect. I expected this as I have had to manually configure 'xorg.conf' for every single Ubuntu release. This time, 'openchrome' seems to have been greatly improved (so I at least boot into a desktop rather than black screen hell)... now just to get the screen configured.

Here is the current situation:
- I created an 'xorg.conf' file (see attached) and I now get the correct screen res when the desktop loads:
- I don't get any splash screen, just black with flashes of pixels, then the GDM login.
- When I log in I get the correct "1024x768" screen res (that's all this panel will run), but I also get an error dialogue stating "x-server does not support the size requested".
- The dialogue disappears, and the desktop seems to function OK. I have not yet tried graphics, acceleration, etc.

Here's what I added in 'xorg.conf':
```
Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    31-48
	ModelName    "1024X768@60HZ"
	Option       "DPMS"
	VertRefresh  50-60
	# V-freq: 60.00 Hz  // h-freq: 47.80 KHz
	# Modeline	 "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Any advice to refine/optimise this setup would be much appreciated...

Thanks,
coady

ATTACHMENTS:
xorg.conf
Xorg.0.log

---

### Post by coady on 2010-05-04
bump...

---

### Post by coady on 2010-05-05
No one...?

---

### Post by amidar on 2011-01-22
i had the same problem and this xorg.conf fixed it

Section "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "openchrome"
Screen 0
Option "SWcursor" "true"
Option "EnableAGPDMA" "True"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1024x768"
Horizsync 31.5-50.0
Vertrefresh 56.0 - 65.0
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
modeline "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1024x768@60" "1280x768@60" "1280x720@60" "800x600@60" "1280x800@60" "800x600@56"
Virtual 1024 768
EndSubSection
EndSection

---

