---
title: "screen resolution 1280*800"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by fred_u on 2006-10-21
Hi,

I'm trying to get my screen resolution right, but I don't quite succeed. 

Specs: Acer Aspire 5003, AMD64, screen resolution 1280*80, refresh rate 60

The relevant part of the xorg.conf file:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
	# 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
	Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
##	SubSection "Display"
##		Depth		1
##		Modes		"1280x800" "1024x768" "800x600" "640x480"
##	EndSubSection
##	SubSection "Display"
##		Depth		4
##		Modes		"1280x800" "1024x768" "800x600" "640x480"
##	EndSubSection
##	SubSection "Display"
##		Depth		8
##		Modes		"1280x800" "1024x768" "800x600" "640x480"
##	EndSubSection
##	SubSection "Display"
##		Depth		15
##		Modes		"1280x800" "1024x768" "800x600" "640x480"
##	EndSubSection
##	SubSection "Display"
##		Depth		16
##		Modes		"1280x800" "1024x768" "800x600" "640x480"
##	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
 
and the Xorg.o.log file says:

(II) VESA(0): Not using mode "1280x800" (no mode of this name)


The funny thing is, when I was using the 5.10 version of Ubuntu, I had no problem in changing the screen resolution. (simply addding "1280x800" to all of the Display SubSections solved the problem) But now, with 6.06 I am not getting it to work. 

Note that I added the Modeline to the Monitor section.

Any suggestions?
Cheers,
Fred

---

### Post by manfromthezoo on 2007-01-23
Ah yes - came across this problem on the Acer 5003, and tried to resolve it the same way as you initially.

In the end, I got it working by re-configuring X, launching from a terminal. I think the syntax is :

sudo dpkg-reconfigure xorg

Although don't quote me on that - it might be slightly wrong (gotta get back to work so can't double check right now).

That'll launch the X setup you'd see if you ran the text based install. I just went through all the options again, but when it gets to the section asking you to confirm what resolutions are supported, you'll notice 1280*800 isn't selected. Just highlight it and press space to select it (an asterisk should appear next to the resolution option). Then accept and complete the rest of the X setup. Close the terminal, and whack CTRL-ALT-BACKSPACE.

Should have done the trick. If not, re-boot. If it hasn't already gone up to 1280*600 automatically (mine did) then you should now be able to pick that resolution in the normal place.....

Good luck! :grin:

---

