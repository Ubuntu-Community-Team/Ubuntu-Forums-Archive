---
title: "Old Problem: Refresh Rate"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by buaa on 2005-08-24
hi all,&#22823;&#23478;&#22909; &#65306;&#65289;

       i'm using 15' LCD Samsung SyncMaster 153v, Kubuntu 5.4. 
  
       The refresh rate in Kcontrol has only one choice: 75Hz. i want to reduse it to 60, what can i do?My video card is I865G,and when i type:  sudo xresprobe i810, it replys:

id: SyncMaster
res: 1024x768 832x624 800x600 720x400 640x480
freq: 30-61 56-75
disptype: crt

      When i make :  dpkg-reconfigure xserver-xorg , there is a screen like this:
[IMG]http://forum.ubuntu.org.cn/download.php?id=754[/IMG]

Can anybody tell me what "particular resolution" means??

here are the sections concerned is  my /etc/X11/xorg.conf
```

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        VideoRam	8000
EndSection

Section "Monitor"
        Option "IgnoreEDID" "True"
	Identifier	"SyncMaster 153V"
	Option		"DPMS"
        HorizSync       30 - 61
        VertRefresh     51 - 75
 # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"SyncMaster 153V"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

thank you !!! &#35874;&#35874;&#65281;&#65281;

---

### Post by evilghost on 2005-08-24
The problem is your modeline isn't being applied because it is called "1024x760_60.00" which isn't being called in your "Screen" section.

To fix this, simply modify your xorg.conf to look like this:
```

Section "Screen"
Identifier"Default Screen"
Device"Intel Corporation 82865G Integrated Graphics Device"
Monitor"SyncMaster 153V"
DefaultDepth16
SubSection "Display"
Depth1
Modes"1024x768_60.00" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth4
Modes"1024x768_60.00" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth8
Modes"1024x768_60.00" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth15
Modes"1024x768_60.00" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth16
Modes"1024x768_60.00" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth24
Modes"1024x768_60.00" "800x600" "640x480"
EndSubSection
EndSection

```

Hope this makes sense.

---

