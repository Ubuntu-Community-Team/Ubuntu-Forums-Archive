---
title: "investing 20 hours fo ATI drivers"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by Proudman on 2007-08-02
hi guys, I'm new to Linux but eager to learn.

I've installed a fresh copy of Ubuntu feisty. The installation went great. Once it booted from my hd i realized that I didn't have 3d hardware acceleration. So how hard can the installing of an ATI 9000 driver be ...........right?

Good thing i know that Ubuntu has a good community so i looked around for any help, and found a lot of articles concerning my problem. 

I've been trying the BinaryDriverHowTo/ati method: 
[URL="https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-4ab0e3d99318196ad8638ba0694fbb8c43a2fbf2"]https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-4ab0e3d99318196ad8638ba0694fbb8c43a2fbf2
[/URL]

after using the code: ./ati-driver-installer-<version>.run --buildpkg Ubuntu/feisty

i got a 165: syntax error: bad substitution
removing temporary directory:fglrx-install"

Looked for a solution:
sudo mv /bin/sh /bin/SH
sudo ln -s /bin/bash /bin/sh

used the same code again and got:
Generating package: Ubuntu/feisty
Requested package is not supported.
Removing temporary directory: fglrx-install

now I'm totally lost here, could any of you guys help me out.

yours truly,

Pavel

---

### Post by eggdeng on 2007-08-02
If you look at the last section of the how-to you linked to, you will see that your card is not supported by the fglrx driver. 

> Prerequisites
The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500

Not to worry, the bundled ati driver is actually very good and supports 3D acceleration. You will be able to run Beryl using aiglx. Check your xorg.xconf ```
sudo /etc/X11/xorg.xconf
``` and make sure you have ```
Driver "ati"
``` in the device section rather than ```
Driver "vesa"
``` Then run ```
glxinfo | grep direct rendering
``` If you get a yes, you've got 3D acceleration.

---

### Post by Proudman on 2007-08-02
First of all, thnx for you fast reply, appreciate it.

Xorg.conf is set as ati from clean install:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

After running glxinfo | grep direct
I still get a NO.

I have also tried putting in "radeon", but i still get NO rendering.

---

### Post by Proudman on 2007-08-02
So basically it knows that i have a Radeon 9000, but Ubuntu doesn't want me to have 3d acceleration?

---

### Post by eggdeng on 2007-08-02
Just to double check you haven't got 3D acceleration, run ```
glxgears
```

---

### Post by Proudman on 2007-08-02
Tried glxgears:

6960 frames in 5.1 seconds = 1368.449 FPS
6960 frames in 5.1 seconds = 1368.341 FPS
6884 frames in 5.0 seconds = 1376.799 FPS
6796 frames in 5.0 seconds = 1358.544 FPS
6947 frames in 5.1 seconds = 1368.176 FPS
6960 frames in 5.1 seconds = 1368.389 FPS
6925 frames in 5.0 seconds = 1384.999 FPS

I'm not familiarized with glxgears, so what can be conluded from these results?

---

### Post by eggdeng on 2007-08-02
Sounds pretty healthy to me. I get about a quarter of that on a box I have running a Radeon 7000 on the ati Driver with 3D acceleration. Are you using XGL? That would explain why you don't get direct rendering even though you do have 3D acceleration.

---

### Post by Proudman on 2007-08-02
Hi there thnx for answering. 

I'm a huge linux newb, so i'm afraid i cant tell. It's a clean install of ubuntu 7.04 with no extra's. Is there a way i can find find out what i am using at the moment?

thnx

---

### Post by myoungf1 on 2007-08-02
Hey there looks like we have the same card and resolutions so I am posting my xorg.conf for you to compare with.  Make sure you have dri loading at the beginning of the conf file and you have the last section for dri as well.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"ATI Radeon 9250"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	128000
EndSection

Section "Monitor"
	Identifier	"ViewSonic 20PS"
	Option		"DPMS"
	HorizSync	30-75
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9250"
	Monitor		"ViewSonic 20PS"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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

---

### Post by Proudman on 2007-08-02
Not seeing anything out of the ordinary. I will post my entire xorg for you guys, maybe you can see whats wrong with my rendering:

 # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by Proudman on 2007-08-02
> **eggdeng said:**
> Sounds pretty healthy to me. I get about a quarter of that on a box I have running a Radeon 7000 on the ati Driver with 3D acceleration. Are you using XGL? That would explain why you don't get direct rendering even though you do have 3D acceleration.

Just took a better look at xorg that i have posted in the previous page and I'm loading XGL. learning new stuff as i go :). What does this mean for direct rendering?

---

### Post by eggdeng on 2007-08-02
Take a look at the post by RAOF on this thread [http://ubuntuforums.org/showthread.php?p=3113297](http://ubuntuforums.org/showthread.php?p=3113297)
I have no experience with Feisty but if you want to run stuff (games) that need direct rendering, the login window should allow you to choose a gnome session without XGL.

---

### Post by Proudman on 2007-08-02
thnx for the information. I'm gonna try that and also try if i can get an other grafix card to work. I;ve got an Ati 7000 card here, so lets hope it will work in one go.

---

### Post by Proudman on 2007-08-02
K guys have an update.

Did a clean install again, then i started a session in just gnome. And got rendering. Then switched back with to x after that session and still had the rendering. Everything works now. Thnx a bunch guys.

Pavel

---

