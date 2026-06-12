---
title: "Trouble with Ubuntu 8.04 ATI Raedeon X300 graphics card."
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by ts2000 on 2008-03-01
In Hardy Heron I have selected the ATI for my Hardware Drivers.  I have XGL working nicely.  No worries.  However, if I log out and log back in my graphics returns with severe out of sync issues and the screen is distorted.

Any ideas anyone?

The relevant portion of my xorg.conf is as follows;


Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  " Display controller: ATI Technologies Inc RV370 [Radeon X300SE]"
	Driver      "fglrx"
#	Busid	    "1:00:1"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

