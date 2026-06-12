---
title: "Upgrade to 7.10 on Sony Vaio made things unhappy"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by mitch_feaster on 2007-11-22
Well I'm pretty much a newbie here but I've got a hunch that when I upgraded to Gutsy from Feisty stuff went wrong.  It seems to be some sort of display driver issue but I don't really know, Here's one sympton for example: as I write this post just having focus be in this text box causes my processor to go up to 100% in use.  If I click out of the text box or if I start highlighting something within the text box the processor usage goes back to normal.
I'm currently using the metacity window manager.  On 7.04 I had compiz running with tons of effects enabled and it was cooking right along without any problems.
I really have no idea what the problem is here so I'm not sure what to include in
this post, but here's a piece of my xorg.conf file:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection




Like I said I don't even know if it's a video driver issue...
Any help is GREATLY appreciated!

---

### Post by Pumalite on 2007-11-22
You should stick to a system that works and you are happy with. People should not feel compelled to upgrade from such a system.

---

### Post by mitch_feaster on 2007-11-22
Yeah I learned that one the hard way...In the mean time anyone have any ideas on how to fix it?

---

### Post by Pumalite on 2007-11-23
Save data and /home and reinstall Feisty.

---

