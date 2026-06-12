---
title: "Set Resolution in Karmic at boot to 1366x768"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SqRt7744 on 2009-10-02
Hi I'm looking to set the resolution of X in Ubuntu 9.10 as the system starts up. I have the problem that the screen defaults to 800x600 unless I tell it to use the native resolution of 1366x768 with the following xrandr commands:

```

xrandr --newmode "1368x768" 85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1368x768
xrandr -s 1368x768

```

I have tried putting these commands in a few places, all of which work... but no matter what I do the resolution is initially 800x600 and only changes to the correct setting *after* X has started. I want it to use 1366x768 right from the start. Any idea in what file I should put those commands?

Hint: it's not
~/.xprofile (that's way too late in the game)
or /etc/gdm/PreSession/Default
or even /etc/gdm/Init/Default 

all of those options, though they work, don't change the resolution until late in the game and lots of unnecessary flickering and stretching occurs. This is bad, especially since this particular ubuntu is powering a HDTV that will be seen by many many people...

any help is appreciated.

---

### Post by Longinus00 on 2009-10-02
Have you tried adding the resolution into xorg.conf?

---

### Post by blakamin on 2009-10-02
Have you tried to set that resolution in grub?

[http://ubuntuforums.org/showpost.php?p=8024427&postcount=17]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17")

---

### Post by SqRt7744 on 2009-10-05
thanks for the grub suggestion, I'll give it a try and let you know how it goes. As far as editing xorg.conf goes, it doesn't exist in karmic anymore...

---

### Post by nanog on 2009-10-05
xorg.conf exists and is used if its generated. its essential for my nvidia setups.

---

### Post by emarkay on 2009-10-05
> **nanog said:**
> xorg.conf exists and is used if its generated. its essential for my nvidia setups.

Can you confirm, I don't see it in a native (clean) install.

---

### Post by SqRt7744 on 2009-10-06
Alright, I got it to work. It turns out that an xorg.conf file can be used if you need one.

I did the following:

1. switch to a console with Ctrl+Alt+F1
2. after logging in, stop X with:
```
sudo service gdm stop
```
3. generate an xorg.conf.new with 
```
sudo Xorg -configure
```
This places a file xorg.conf.new in your home directory.
4. copy the file to /etc/X11/xorg.conf
```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
```
5. edit /etc/X11/xorg.conf to your needs, in my case (for 1366x768 ) it looks like this:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri2"
	Load  "record"
	Load  "glx"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	ModeLine     "1368x768" 85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Modes "1368x768"
		Viewport 0 0
		Depth     24
	EndSubSection
EndSection

```
6. I'm not sure if this is 100% necessary, but I did it anyway, and this is to tell X to use the new xorg.conf. To this end I edited the file
/etc/X11/xinit/xserverrc to read:
```

#!/bin/sh

# $Id: xserverrc 189 2005-06-11 00:04:27Z branden $

exec /usr/bin/X11/X -config /etc/X11/xorg.conf -nolisten tcp


```
...note the -config line.

7. joy of non-flickering startup


p.s. I also tried the grub method, but no joy, the settings from grub aren't passed to X.

---

