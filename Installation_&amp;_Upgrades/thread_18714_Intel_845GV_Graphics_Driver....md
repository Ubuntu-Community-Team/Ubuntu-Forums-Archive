---
title: "Intel 845GV Graphics Driver..."
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by total-noob on 2005-03-08
Everything works fine, but could someone confirm that everything is setup correctly. My Warty Ubuntu box has onboard Intel 845GV video and it works fine with 1280x1024 resolution and 24 bit. I read that i845G is supported by the i810 driver included in XFree86 4.3.0:
[INDENT]
[www.xfree86.org Intel status...](http://www.xfree86.org/4.3.0/Status17.html#17)[/INDENT]

When looking in /etc/X11/XF86Config-4, I see this:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"hp L1702"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

To me this looks okay. Do I need to do anymore? Running Tux Racer is not that nice, with large triangles flashing now and then.  Trying out Flight Gear was quite dissapointing.  8-[ 

Should I move on to Intel driver downloads?

[Intel 845G driver downloads...](http://downloadfinder.intel.com/scripts-df/filter_results.asp?strOSs=39&strTypes=DRV%2CARC&ProductID=865&OSFullName=Linux*&submit=Go%21)

---

