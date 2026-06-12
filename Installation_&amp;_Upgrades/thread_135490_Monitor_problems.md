---
title: "Monitor problems"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by jpearson on 2006-02-23
Hello,
After installing Ubuntu I receive an error message stating that graphics system could not start and that I need to configure it manually.  My monitor is a Sceptre Ultra High Speed flat panel.  I was wondering how I go about doing this.  Any help would be greatly appreciated
Thank you in advance
John

---

### Post by andrewsawyer on 2006-02-24
Try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
from the command line.

---

### Post by jpearson on 2006-02-24
Thank you very much for your quick reply.  I tried the command you suggested and received a screen in which I could change the resolution.  I tried changing and it did not help.  I still receive the error stating that the X server could not init.  When this occurs I am given the option to view a log.  In this log it states:
Radeon screen init failed
Radeon XAAinit error.
My graphics card is a Radeon Xpress 200 series if this helps.
Thank you
John

---

### Post by andrewsawyer on 2006-02-24
I've found in cases like these it may be simpler to do it manually.  Type the following into terminal:

```
sudo gedit /etc/X11/xorg.conf
```

In the config file that loads up, scroll down to 'SubSection "Display"', and just manually type in the resolution that you want to run at.  I'd list mine, however I'm running in Twin View mode, so it probably wouldn't help much.

---

### Post by jpearson on 2006-02-24
Hello once again,
  I did as suggested and I still have the same error popping up.  One thing I noticed is in the display section it states "Generic Display".  Does this make any difference that my display is a flat panel?  It does list my graphics card  correctly so that is a plus.  
I am new to Ubuntu Linux so I am not familiar with having to do all this.  
Thanks for the help
John

---

### Post by andrewsawyer on 2006-02-24
Hmmm... this may then be a Radeon driver issue.  I'm using nVidia here, although I have grabed a couple of outputs from two laptops for you to have a look at - I hope this might help you...

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x768"
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

```
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
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

---

### Post by jpearson on 2006-02-25
thank you for taking the time to post all of that.  I check the file and everything looks good.  Not exactly sure what is going on.  Hopefully someone else has some ideas.  
John

---

### Post by Irony on 2006-02-25
Is the section that says;

[PHP]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection[/PHP]

correct for your monitor - you'll need the correct *HorizSync VertRefresh* numbers for your monitor.

---

### Post by jpearson on 2006-02-27
I ran the program as suggested, got the information, entered it into the xorg.conf file and I still get the same error.  I was reading the log file and this is what it says:
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o"  no               
             symbols found
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o"  no               
             symbols found
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o"  no               
             symbols found
skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o"  no symbols found
(EE)Radeon(0):[dri]DRIscreeninit failed Disabling DRI
(EE)Radeon(0):XAAInit error
Fatal Service error Caught Signal 11. Server aborting.

That is it.  I am totally and utterly confused.
Thank you
John

---

### Post by thediviner on 2006-04-05
Greetings,

I also have the Radeon Xpress 200 series and was having this exact same problem. I found a tip [here]("http://www.ubuntuforums.org/showthread.php?t=140421&highlight=%22caught+signal+11%22")

The relevant part is to add Option "NoAccel" "True" in the device section. That seemed to allow X to start for me. I hope that helps.

---

### Post by jpearson on 2006-04-05
Thank you very much.  I will give that a try.
John

---

