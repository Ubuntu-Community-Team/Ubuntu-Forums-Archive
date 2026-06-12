---
title: "highest resolution not working in gutsy for ATI radeon 7200"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by lunatic77 on 2007-10-24
I have just upgaded to Kubuntu Gutsy, and everything went seemingly very well, except for the 1680x1050 mode for my video card which is an ATI Radeon 7200 (R100).  The card was detected automatically and is detected correctly when I run dpkg-reconfigure xserver-xorg.  The specific symptom is that, in 1680x1050 mode, about the right 1/3rd of my screen is black, and the rest of the screen has a squished apsect ratio. It happens exactly the same way when I boot via the LiveCD.   Here is the excerpt from my xorg.conf:

```
Section "Device"
   Identifier  "ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
   Driver      "ati"
   BusID    "PCI:1:0:0"
   Option      "UseFBDev"     "true"
EndSection

Section "Monitor"
   Identifier  "AL2223W"
   Option      "DPMS"
   HorizSync   31-81
   VertRefresh 56-75
EndSection

Section "Screen"
   Identifier  "Default Screen"
   Device      "ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
   Monitor     "AL2223W"
   DefaultDepth   24
   SubSection "Display"
      Modes    "1680x1050" "1600x1200" "1440x900" "1280x1024" "1280x960" "1280x800" "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

```

The rest of the video modes work fine.  Thanks in advance for any help you might be able to provide!

---

### Post by jpl80 on 2007-10-29
I have the exact same card and I've double checked all of the settings. Did you ever get anywhere with this?

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
	Driver		"ati"
	BusID		"PCI:01:00:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

```

I had it working on 7.04. but now that I upgraded to 7.10, it's broken.

---

### Post by Tulsapoke on 2007-10-30
I have this exact problem  also (squished image to the left with a black bar on the right). 

Monitor: AL2223W
Vid card: ATI Technologies Inc Radeon R100 QD [Radeon 7200]

Worked fine under feisty with following settings in xorg...

```
Section "Monitor"
Identifier "AL2223W"
HorizSync 31 - 82
VertRefresh 56 - 75
Option "DPMS"
Modeline    "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
	Monitor		"AL2223W"
	DefaultDepth	24
	SubSection "Display"
       		Depth       8
        	Modes       "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        	ViewPort    0 0
	EndSubSection
	SubSection "Display"
		Depth 	    24
		Modes 	    "1680x1050" "1600x1200" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
        	ViewPort    0 0
	EndSubSection
EndSection

```

My parents have the same monitor as I do and they have had the same problem even with a different video card, so am leaning towards that this is some sort of issue with the monitor and Gutsy.

Please post if you figure out a fix.

---

### Post by lunatic77 on 2007-10-30
How's that for a string of coincidences: I graduated from OSU and am living in Tulsa, and I have the exact same monitor and the same video card!

A friend of mine suggested that possibly the HorizSync or VertRefresh was incorrect for my monitor.  I toyed with it and now 1440x900 is ok but 1680x1050 is still messed up.....

:confused:

---

### Post by Tulsapoke on 2007-10-31
Amazing coincidence!

I think you may be right regarding the monitor synch settings.  I have been looking though the available monitors under the screen and graphics preferences and they don't have this monitor, nor anything close to it.  I looked around the web for a .inf file and cant find any for this monitor.  It sounds like this .inf file may be just a listing of settings so maybe it is possible to create one since I know my old xorg settings worked fine. Then use the import inf file button to get the right settings in.

I tried initially to just reuse the portions of my xorg.conf file that worked with Feisty however this breaks X and I have to replace the xorg with the backup to get to at least get to a blurry desktop.

Man I hope someone can figure this out, this is killing my eyes.  Too much more of this and I will have to go back to Feisty. 

-Go Pokes!

---

### Post by Tulsapoke on 2007-10-31
I found a setting for xorg.conf that forces it to use the modeline you give it instead to the gui setup.  This _completely_ fixed it for me.

```
Section "Monitor"
	Identifier	"AL2223W"
	Option		"DPMS"
	Option		"DDC"	"false"
	HorizSync 31 - 82
	VertRefresh 56 - 75
	Modeline 	"1680x1050" 149 1680 1784 1960 2240 1050 1053 1059 1089
EndSection
```

This Option "DDC"  "False" evidently forces it to use the modeline and then this modeline seems to work for me.  I still had to fiddle with getting the monitor to auto fix to set it perfect but it is good to go now.

---

### Post by lunatic77 on 2007-11-10
Thanks I'll try that when I get a chance!

---

### Post by sysanalyst on 2007-11-14
Same issue here, tried both an ATI 7000 and ATI 7200 AGP card at 1680x1050 under Gutsy with no success. Both cards run fine under:KS Feisty :KS at 1680x1050.  Have a spare 9800 AIW Pro AGP that I'll be testing out in the near future. Have tried all of the listed fixes with no success.  If the 9800 AIW Pro doesn't work, I'll be going back to Feisty. Any fresh ideas? :confused: Oh yes, monitor is an Acer 22 wide screen using the analog port.

---

### Post by sergio_101 on 2008-02-20
just for the record, the above worked for me..

that was driving me crazy..

but the inclusion of the following lines made it all better:

	Option		"DPMS"
	Option		"DDC"	"false"

---

