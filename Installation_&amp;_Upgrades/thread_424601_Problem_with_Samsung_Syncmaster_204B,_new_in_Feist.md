---
title: "Problem with Samsung Syncmaster 204B, new in Feisty."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Rashind on 2007-04-26
Hi, here's my little story...  

I've been waiting for the final release of Feisty, and I finally got around to installing it.  I'd been running Edgy with no real problems.  I decided to just dump everything on the computer (backed up my important stuff, of course), and do a fresh install with the 7.04 32-bit DVD.  Everything seems to be going okay, except it's not running my monitor properly!  

The relevant hardware in play are an eVGA 8800 GTX, and a Samsung Syncmaster 204B.  

I'd like to stress that everything was fine with Edgy.  Of course, I'd had to install the relevant proprietary drivers, but everything was working great once I got that taken care of.  Now it almost-works right out of the box, except my monitor keeps complaining that it's not at optimal resolution (1600x1200@60), even though according to everything I can find in the "screen resolution" app under System -> Preferences and /etc/X11/xorg.conf it IS at 1600x1200@60.  Yet, not only does the monitor complain, it also has two unsightly black bars at either side (about a centimeter on either side.)

Does anyone have any idea how I can fix this?  I've tried a few things on the forums responding to similar-ish problems (nobody seems to have my exact problem), but all that's gotten me is a couple of reinstalls.  In particular, I tried using the nVidia drivers with the restricted drivers manager, which just kills X windows on restart, leaving me to reinstall yet again.

In case it helps, here's my xorg.conf file.  It's a bit messy at the moment, since my most recent attempt involved telling the installer to try every possible video mode.

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTX]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTX]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Rashind on 2007-04-27
No one has any help for me?  Aw, shucks.

Well, I tried installing the 9755 nVidia drivers according to these [http://ubuntuforums.org/showthread.php?t=336412]("http://ubuntuforums.org/showthread.php?t=336412") instructions.  The new kernel it built wouldn't run X at all.  I guess I'll just have to reinstall and deal with the weird monitor behaviors for now.

---

### Post by roachk71 on 2007-04-27
You might want to try removing these resolutions from your mode lines:
```
"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050"
```

It would appear those are outside the monitor's range.

---

### Post by Rashind on 2007-04-27
> **roachk71 said:**
> You might want to try removing these resolutions from your mode lines:

Yup, currently running with only the 1600x1200 modeline.  Those extra modelines were a relic from my brain-fart of "Well, gee, if telling it to run at 1600x1200 makes it run at 1500x1200 (I guess...), maybe telling it to run at something higher will actually give me 1600x1200!"  Didn't pan out, by the way.

---

### Post by roachk71 on 2007-04-27
Hmm... This might be related to your default card settings:
```
Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTX]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection
```

Try changing this to:
```
Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTX]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
        Option          "DDCMode"
EndSection
```

and see if that helps.

Of course, some nVidia cards have a problem using the DDC probe...

---

### Post by Rashind on 2007-04-27
> **roachk71 said:**
> 
Try changing this to:
```
Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTX]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
        Option          "DDCMode"
EndSection
```

and see if that helps.

Of course, some nVidia cards have a problem using the DDC probe...

Just saved that changed and ctrl-alt-backspaced... same old story.  =(  Thanks, though.  Any new thing to try is great.

---

### Post by roachk71 on 2007-04-27
I'm on the IRC channels looking for help right now, and I'll get back to ya in a few.

---

### Post by roachk71 on 2007-04-27
The channel's bot just pointed me to the Binary Driver Howto.

Here's a link that might help you out more than I can here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Rashind on 2007-04-27
Thanks.  I'll delve into that and post back here whether it works out or not.

---

### Post by Rashind on 2007-04-27
> **roachk71 said:**
> The channel's bot just pointed me to the Binary Driver Howto.

Here's a link that might help you out more than I can here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Curses!  I tried the horizsync/vertrefresh values I was able to find online...  I tried several sets, none of them hurt or helped.

I also tried using enabling the restricted driver with the new Feisty thing (which I've tried before, but what the hey...), and of course X wouldn't start up with it... again...  Gotta reinstall again, now.

If anyone has more ideas, I'm subscribed to this thread.  Even if someone has new ideas for getting an nVidia driver working, that'd be fantastic.  If I could have 3D acceleration from my 8800GTX, I'd be a happy man.

---

### Post by roachk71 on 2007-04-28
If you're looking for better acceleration, here's a little help:

```
Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTX]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
        Option          "AGPMode"            "4"
        Option          "AGPFastWrite"     "enable"
        Option          "RenderAccel"       "true"
        Option          "AccelMethod"       "EXA"
        Option          "DDCMode"
EndSection
```

This only applies to 2-D acceleration, but you will have a faster display than the default settings. If the X server complains, try removing the AccelMethod line; some cards don't support it. Sorry I can't help much on this subject (my video chipset is an integrated model from ATI, and some cards and monitors aren't correctly supported either by X, or by the proprietary driver.)

---

