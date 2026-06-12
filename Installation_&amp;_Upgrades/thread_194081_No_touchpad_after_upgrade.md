---
title: "No touchpad after upgrade"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by bill_wad on 2006-06-10
I just updated my HP omnibook 900 to 6.06 from 5.10 and everything seems to be working except the touchpad.  I can get around w/ the keyboard stick thingy but I need my touchpad.  My xorg.conf has the touchpad configured.  The section of the file that relates to this is:

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

Any ideas on why my touchpad isn't working w/ dapper?

Thanks in advance

-B

---

### Post by jbrader on 2006-06-11
You probably need to add:

```
Section "InputDevice"
        Identifier      "touchpad"
        Driver          "synaptics"
EndSection 
```

to xorg.conf.

P.S. Credit for this fix (assuming it works) should go to [joske]("http://ubuntuforums.org/member.php?u=75594") and not to me.

---

### Post by jbrader on 2006-06-11
Sorry you already have that I guess I need to read better. Try adding this line:

```
InputDevice     "touchpad" "AlwaysCore"
```

to the ServerLayout section of xorg.conf

---

### Post by bill_wad on 2006-06-14
Thanks for the advice but no go.

Since the advice is focused on xorg.conf I thought I'd copy the whole file in case someone can see my issue.  

One question I have is - I thought that I'd see a different entry for the keyboard stick?  I don't see it - so how is it that this works?

Thanks,

-B

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
	Identifier	"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Driver		"neomagic"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Synaptics Touchpad" "AlwaysCore"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by bill_wad on 2006-06-17
A little more info on this problem.  In checking around I found this in the xorg.log file:

(II) Synaptics touchpad driver version 0.14.3
Synaptics Touchpad no synaptics event device found (checked 13 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

So it looks like there is a more basic problem than the xorg.config file.  The touchpad worked before updating to 6.06 dapper. 

Any ideas? :confused: 

-B

---

### Post by bill_wad on 2006-06-25
Any help on this?  ](*,)

---

### Post by LazyP on 2006-06-27
Try adding the following after Section "Module"
        Load    "synaptics"

if that doesn't help then add into your synaptic device section
  Option        "SHMConfig"     "on"

and then install qsynaptics (available in synaptic). You might have to start qsynaptic when you start the computer to get the touchpad to work correctly

---

### Post by bill_wad on 2006-06-28
Thanks for the advice.  I tried the first two changes - no luck.  I tried to install the qsynaptics module and I cannot find it in synaptics.  Is this package not yet up for 6.06?

-B

---

### Post by rgreves on 2006-07-02
Hey wad -- 

Same problems here, except I went from WinNt 4 (which came with the laptop) to Xubuntu.

No touchpad, no audio. 

Everything else is great though. My D-Link DWL-G630 popped right up and got me on my network, and the XFCE desktop screams along on this teeny tiny laptop. (Even my Ipod Nano was found!)

I have tried several different setting for the touchpad following the thread, and mine doesn't work either.

My setup is: HP Omnibook 900, PII - 400MHz, 160 MB Ram, Xubuntu 6.06

---

