---
title: "Screen resolution and refresh rate."
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by glore2002 on 2007-03-24
Hello!
I've just bought a LCD analog monitor (Samsung 732NPlus). Since the max resolution for Ubuntu 6.10 was 1024x768, I changed xorg.conf to be able to display at 1280x1024. I've added HorizSync and VertRefresh as well as the new resolutions in the screen section.

Now, it works ok but the refresh rate is set to 75Hz without any other possibilities (only 75Hz). 

Since the recommended resolution for this monitor is: 1280x1024 and 60Hz,** I would like to have the possibility to choose between 75 and 60Hz to see which one looks better.** What should I add to xorg.conf? 

I will really appreciate if you could help me solve this. Thank you.

**This is my xorg.conf **(the sections that correspond to Monitor and Screen)

Section "Monitor"
	Identifier	"Samsung SyncMaster 732NPlus"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de video genericanvidia fx5500"
	Monitor		"Samsung SyncMaster 732NPlus"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by heimo on 2007-03-24
Not sure if this will work, but you could try adding custom modelines, more information on this [URL="http://www.ubuntuforums.org/showthread.php?t=83973"]Howto
[/URL]

---

