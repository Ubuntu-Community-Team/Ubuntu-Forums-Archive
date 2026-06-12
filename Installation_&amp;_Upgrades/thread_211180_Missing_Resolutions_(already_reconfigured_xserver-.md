---
title: "Missing Resolutions (already reconfigured xserver-xorg)"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by jan247 on 2006-07-07
I'm on a Dell 9400 laptop, with a WUXGA screen and an ATI Radeon X1400. I understand that there is no driver yet for the card, but I was expecting to get the proper resolution for this. The max resolution I can get is only a 1600x1200. Here's a section of xorg.conf

-----------
Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1200x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
-------------

Also, when I change resolutions, GDM restarts. Can anyone help?

---

### Post by cacharreo on 2006-07-08
I think the problem is that you are uusing the ***vesa*** driver, and you should use an specific ATI driver. Try from ATI web site there you'll find specifics linux drivers.
[www.ati.com](www.ati.com)

---

### Post by PriceChild on 2006-07-08
I'm sure you could still try using the standard ati driver, look for a guide on the forums :S

---

