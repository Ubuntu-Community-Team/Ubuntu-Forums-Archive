---
title: "Changing refresh rates in xorg.conf crashes X"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Dubra on 2007-11-04
I can't find mention of this issue anywhere online, so here goes:

   I am running Gutsy and have successfully installed the new ATI proprietary drivers with AIGLX, not running GLX.  Compiz works!  3D apps (Urban Terror 4, Scorched 3D) have a serious flicker problem.  Previously I had this same setup working and was able to change the Horizsynch and VertRefresh in my xorg.conf.  This allowed much better performance in 3D.  After a fresh install to setup my /home directory on a separate drive I have some issues.

My first xorg.conf looked something like this:
> Section "Device"
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"L90D+ DVI"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"L90D+ DVI"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
    I was able to simply add my refresh rates to the "monitor" section and it was perfect.

    My NEW xorg.conf looks like this:
> Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection


     After the fresh install of OS and drivers I have the same flicker problem, but changing  the monitor specs in any way in the file crashes X and sends me to "low graphics mode".  I have spent two days trying various changes in xorg.conf (always saving a backup) but everything crashes X.  When I run ddcprobe it seems to recognize my monitor but sees it as analog.  It is DVI.  ddcprobe spits out all of the resolutions and refresh rates the monitor would have as analog.  Plugged in DVI it can't go beyond 60Hz though.  I was thinking that, somehow, ddc is not recognizing my monitor corretcly.  Tried turning that off in xorg.conf and...crash.  Installed get-edid through synaptic and it seemed OK but I have no clue what I should be looking for.  

   I'm a complete noob (less than two weeks into my Linux experience) and I'm over my head.  Is this flicker just a fact of life with these drivers?  If so, why does xorg.conf puke when I make those simple changes?

Other info:  MSI K9VGM-V mobo, AMD 64 4000 cpu, miserable ATI X600 PCI-E card I grabbed off WOOT

  thanks for reading, sorry I went on so much,

Dubra

---

### Post by TechnoJunky on 2007-11-15
have you tried using the gui in System Settings to make your changes?  You might find it much easier than modifying the xorg.conf file manually.

---

