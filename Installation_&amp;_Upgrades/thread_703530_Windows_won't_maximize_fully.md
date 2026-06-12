---
title: "Windows won't maximize fully"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by kosta008 on 2008-02-21
I'm running Ubuntu 7.10.  None of my windows maximize to the full height and width of my screen.  If I hit the maximize button the window jumps to the upper left hand corner and gets a little bigger... that's it.  I have about an inch border on the right and bottom of the screen.  It just won't maximize all the way.  Any ideas?

---

### Post by kosta008 on 2008-02-22
Anyone?? This is driving me nuts...

---

### Post by banewman on 2008-02-22
Have you tried putting the cursor in the bottom right of the window and dragging it out to full size then seeing if it maximizes properly the next time you open it?
:)

---

### Post by kosta008 on 2008-02-22
Yeah, I tried that.  It's so wierd, if I move the entire window down to the bottom right and then click the maximize button, it does maximize fully.  But then when I hit any button, or link for example in firefox, the window jumps back like the picture attached to this thread.  The window does not want to remember it's location or size.  My screen resolution is set to 1400x1050, the only thing that looks right.

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by Therion on 2008-02-22
Total stab in the dark here since I'm at work (and stuck behind a Windows box) but I see you've got Compiz Fusion running (the multiple desktops)... Isn't there a plugin for Compiz that deals with this... "Resize Window" or "Windows Manangement"... Something like that?  Sorry I can't be more specific, but this just reeks of a Compiz' setting being out of whack.

Ahhh... I'm thinking of the "Resize" plugin.  Don't know if it's the answer to your problem, but that's the plugin I was trying to think of...

---

### Post by kosta008 on 2008-02-22
Yup, I saw those... One is "Resize Info" that is not enabled, it seems to provide information while resizing a window.  The other is "Resize Window" which is enabled.  If I disable it, I just can't resize windows at all.  There doesn't seem to be any settings there, though, to fix my problem.  It's a pretty simple and bare plugin.

---

### Post by kosta008 on 2008-02-24
This is so frustrating... I still can't figure it out.  Should I try a different video card driver?

---

### Post by maaylix on 2008-05-11
kosta, do you by any chance have more than one monitor or tv hooked up?

I was having the exact same problem here when I switched from ''none'' to ''normal'' visual effects in ''appearance''  

I had my tv hooked up via S-Video cable and I had it configured to run in ''Twin View'' mode

Thing is my TV has a lower max resolution compared to my monitor (1280x1024 & 1024x768 ). Compiz  was resizing windows to fit my tv resolution.

Once I disabled Twin view and left only my monitor to work the problem was solved

Well sort of... I would like to keep my TV in Twin view mode and not have compiz resize everything to fit my tv, anyone know how to fix this?

---

