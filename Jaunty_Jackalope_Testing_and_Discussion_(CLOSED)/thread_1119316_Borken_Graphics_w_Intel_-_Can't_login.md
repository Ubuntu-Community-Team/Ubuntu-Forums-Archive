---
title: "Borken Graphics w/ Intel - Can't login"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zerted on 2009-04-07
I updated my X61 Tablet and it can no longer display the login screen.  The display is just blank.  The loading cursor flicked on and off for a moment, but that is it.  Switching to another screen (Ctrl+Alt+3) doesn't seem to do anything.

I noticed [this topic]("http://ubuntuforums.org/showthread.php?t=1099480") about a similar problem, but I am not using any ATI hardware.  I don't even have xorg-driver-fglrx installed.  I think the tablet uses the Intel 965 Express Chipset.

Edit: Using the 'fix graphics' recovery option seems to have fix the problem, so I'll assume the problem had something to do with my xorg.conf file?  Here is the fixed version:```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```And here is the broken version (which worked fine before the updates):```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2800 1050
	EndSubSection
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option	"Device"	"/dev/ttyS0"
	Option	"Type"	"stylus"
	Option	"ForceDevice"	"ISDV4"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "eraser"
	Option	"Device"	"/dev/ttyS0"
	Option	"Type"	"eraser"
	Option	"ForceDevice"	"ISDV4"
EndSection

Section "InputDevice"
	Driver	"wacom"
	Identifier	"cursor"
	Option	"Device"	"/dev/ttyS0"
	Option	"Type"	"cursor"
	Option	"ForceDevice"	"ISDV4"
EndSection

Section "ServerLayout"
	Identifier    "Default Layout"
	Screen        "Default Screen"
	InputDevice   "stylus"  "SendCoreEvents"
	InputDevice   "eraser"  "SendCoreEvents"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Interestingly, my tablet pen now seems to be working without the wacom InputDevice section.  I don't know it that is related...  9.04 isn't going to have MPX support (or whatever it's called now) correct?

---

### Post by Favux on 2009-04-07
Hi zerted,

Well your new xorg.conf video sections seem to be in a better order at least.  So you're thinking the new Xorg Intel driver with Jaunty didn't like something about your virtual subsection?

The acid test will be adding the Wacom stuff back in.  You do not need the Wacom cursor section because you don't have a Wacom mouse. I'd suggest putting stylus and eraser above the video sections and putting "ServerLayout"  below them.  Notice you didn't have "cursor" in "ServerLayout".  I don't know if that was enough of a format error to break X.

---

### Post by trot2millah on 2009-04-07
There have been general problems with X.org and Intel drivers for the most part in this release, glad you worked this one out.  I'm still unable to run Jaunty on my old desktop with an i845 card >_<

---

### Post by cywhale on 2009-04-08
Had the same problem with blank login screen - after 
- editing xorg.conf 
  - commenting out the wacom devices and 
  - commenting out ServerLayout section
  - setting UXA (just for testing)

everything works fine again with Travelmate C110/Intel 855GM.

---

