---
title: "screen resolution issue"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by upalm on 2005-05-03
hi,
i'm using an older 266mhz NEC 6260 with 64mb RAM laptop.  my resolution is 800x600 but the picture on the screen takes up only about 2/3 of the screen and is positioned top left. I tried the Fn+Display key to try to change it but no luck. My graphics controller is a NeoMagic NMG4.
any pointers much appreciated.
thanks
upalm

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=upalm]hi,
i'm using an older 266mhz NEC 6260 with 64mb RAM laptop.  my resolution is 800x600 but the picture on the screen takes up only about 2/3 of the screen and is positioned top left. I tried the Fn+Display key to try to change it but no luck. My graphics controller is a NeoMagic NMG4.
any pointers much appreciated.
thanks
upalm[/QUOTE]


I had a porblem like this with an old laptop. Try this:

sudo gedit /etc/X11/xorg.conf

find this part:

> Section "Screen"
	Identifier	""
	Device		""
	Monitor		""
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection 

Change the default depth to 16 like this:


> Section "Screen"
	Identifier	""
	Device		""
	Monitor		""
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by upalm on 2005-05-04
worked a treat! thanks very much for your help - linux is a lark! O:)

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=upalm]worked a treat! thanks very much for your help - linux is a lark! O:)[/QUOTE]


No problem...

---

