---
title: "Laptop / ATI Problems"
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by Jabustabin on 2005-02-21
Hello,
I have a Dell 8000 Laptop with an ATI Mobility M4 32MB video card.  I just installed warty on it last week.  Everything loaded fine and x started right away.  Everything seemed to be running fine at 1024x768.  I tried smaller resolutions but the screen was garbled.  I really do not care to get the hardware acceleration working since I do not take advantage of it.  Here is the problem.  After shutting down and rebooting, X appeared to be trying to load and then my laptop screen went haywire.  The entire screen turned a green color and then faded to yellow.  I have never seen this before on my laptop.  I rebooted into recovery mode and ran:

dpkg-reconfigure xserver-xfree86

Made some changes: Disabled the loading of dri, glcore, glx modules

Rebooted and x started up.  I thought everything is fine and went on working.  Then I hit the logout button on the desktop to shutdown and the screen freaked out again like it had before.

So, I rebooted into recovery, opened the config file in emacs and edited the sections to default to a depth of 16 and deleted all other sections for depths.  However, I noticed that the glcore and glx modules were still listed as being loaded.  I tried the dpkg-reconfigure again and selected the vesa drivers, rebooted and x booted into that same freaky screen again.  I rebooted again into recovery mode and looked at the config and noticed that it still said the ati driver was being loaded along with the glcore and glx modules.

I am at a loss at this point.  It doesn't seem like the reconfigure command is actually making changes to the config file.

Any help would be appreciated.  I really don't want to go back to SuSE.

Here is my XF86Config-4:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M4 (AGP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-60
	VertRefresh	60
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M4 (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tyze on 2005-06-07
Try to boot Ubuntu in normal mode, then press ctrl + alt + 3 ... normally you will come now into a console... just log in and then edit the /etc/X11/xorg.conf or /etc/X11/XF86config-4 there. Maybe the changes will be accepted then.

---

