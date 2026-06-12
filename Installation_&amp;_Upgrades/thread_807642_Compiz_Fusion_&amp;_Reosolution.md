---
title: "Compiz Fusion &amp; Reosolution"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by orix on 2008-05-26
I have installed the Nvidia Driver to run Compiz Fusion on 8.04 Ubuntu.  I'm using a Dell SE198WFP with a GeForce4 card.  I changed the xorg but can only get with Fusion a resolution of 800x600 but changing the xorg from Nvidia to Vesa I can have any resolution I want. Is there anyway to get both.  

//This will allow me to have Fusion//
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

//This allows me to have a higher resolution"
Section "Device"
	Identifier	"Configured Video Device"
        Driver		"vesa"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "1280x1024"
	EndSubSection
EndSection

I tried combining the Screen part but to no avail.  

This did not work

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes   "1280x1024"
	EndSubSection
EndSection

---

### Post by iaculallad on 2008-05-26
Try replacing your "Device" and "Screen" section with this and restart.

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

and at the "Monitor" Section, add the line of text that does not have any asterisk on it.

*Section "Monitor"
*Identifier "Configured Monitor"
HorizSync 30-110
VertRefresh 50-160
*EndSection

This could solve your problem.

---

### Post by orix on 2008-05-26
I changed the Xorg and it have the compiz features but with low resolution still.

---

