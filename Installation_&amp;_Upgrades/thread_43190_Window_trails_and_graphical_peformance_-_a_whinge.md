---
title: "Window trails and graphical peformance - a whinge"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by geokker on 2005-06-21
Why is the desktop gui so slow? I have a 1GHz PIII, plenty of RAM, a quick drive and a corectly installed 128MB Nvidia Geforce AGP graphics card. When I drag a window about on the screen, I get the 'cursor trails' effect reminiscent of an ancient Windows 95 machine. Surely, I shouldn't be experiencing this?

I assume the graphics card is not being utilized for the gui. So, is there a way to use the power of the graphics card to draw the screen? I think I deserve quick, fast windowing after all, it's now the 21st century!

- Don't even get me started about the horrific 'minimize' animation - although I am resigned that this cannot be removed without also losing dragging visible windows. (Pulsing a freshly minimized window in the taskbar would be a better idea.)

---

### Post by geokker on 2005-06-22
And yes, I know about the reduced_resources tweak - but the wireframe is even uglier. + Everyone but everyone constantly repositions windows - we probably shouldn't - but we do.

---

### Post by nocturn on 2005-06-22
Dit you install the Nvidia drivers and nvidia-glx?

can you try to run glxgears (or glgears, not sure) to see the framerate?

What does your xorg.conf look like?

---

### Post by geokker on 2005-06-22
Bearing in mind that this is a whingey moaney whine, here is my config.

A ditched windows XP because of little, minor irritations like clicking the start menu and waiting a few seconds for the menu to pop up - thankfully, that isn't happening with Gnome. The screen redraw rate is annoying. That 128MB of GPU must be exploited.

Yes, I have a 1600x1200 rez - but still...

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"iiyama Vision Master 1451"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	30-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4400]"
	Monitor		"iiyama Badass Gangsta Vision Master 1451"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
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

---

