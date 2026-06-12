---
title: "Better refresh rate than 51?"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by xl_cheese on 2007-06-05
I've finally got my nvidia 8600gt card working with ubuntu.

Now I want to set the refresh rate high, but there is no option for.  I've searched the forums and have tried everything I could find.  did the reconfig xserver thing and have manually edited the xorg.conf file.

Here's what it looks like:
Section "Monitor"
	Identifier	"Dell SE197FP"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	40-100
# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia 8600gt"
	Monitor		"Dell SE197FP"
	DefaultDepth	24
#	SubSection "Display"
#		Depth		1
#		Modes		"1280x1024" "1024x768" "800x600" "640x480"
##	EndSubSection
#	SubSection "Display"
#		Depth		4
#		Modes		"1280x1024" "1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		8
#		Modes		"1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		15
#		Modes		"1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		16
#		Modes		"1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_75.00"
	EndSubSection
EndSection

---

### Post by logos34 on 2007-06-05
It may be running at 75hz even though it says 51...I have a problem where my refresh rate under System>Prefs>screen resolution says 52 but it's really set to 85Hz (I'd definitely notice the flicker if it was way down in the 50's... In a terminal:

nvidia-settings

Click "X server display settings" and set the refresh there.  Then go back to Screen res and make sure it's checked as default and hit ok.

This works using the nvidia-glx binary driver (although after setting it in nvidia-settings it shows up as '130Hz' for some reason, but at least it stays there)...I just managed to get in the 9746 driver and I notice my screen res refuses to show the actual rate.

---

