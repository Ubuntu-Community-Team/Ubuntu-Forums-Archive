---
title: "Gutsy and 82865G Integrated Graphics Controller"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by andrew.46 on 2007-09-28
Hi,

 Running the beta of Gutsy an loving it. But I am suddenly unable to run xv video under mplayer. The error is:

> [VO_XV] It seems there is no Xvideo support for your video card available.


 Which is crap as I have run this mode before :) I suspect my 82865G Integrated Graphics Controller has been perhaps misidentified in xorg.conf but before I write up a bug report can I ask if this is the standard settings for such devices:

> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E153FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"DELL E153FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

 Thanks for any help!

              Andrew

---

