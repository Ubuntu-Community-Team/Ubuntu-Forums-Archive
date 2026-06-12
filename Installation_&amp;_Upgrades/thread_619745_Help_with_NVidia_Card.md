---
title: "Help with NVidia Card"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by jaywatkins on 2007-11-21
Hello,

I have an old beige box with a fresh install of Gutsy on the hard drive.  The video card is an NVidia GeForce FX 5700 with 256MB of RAM, attached to a Dell P780 17" CRT.  The current resolution is 640x480.  I would like to up that to 1024x768, and/or install the NVidia drivers.  Editing xorg.conf did not get me to the target resolution.  Is there a relatively simple way to get the NVidia drivers up and running?

Thanks

/J

---

### Post by PmDematagoda on 2007-11-21
Open up the Nvidia settings using:-

```
sudo nvidia-settings
```

go to X Server Display Configuration and set the resolution to what you want, then save to X configuration file and see if you can get the resolution you want.

---

### Post by jaywatkins on 2007-11-22
Hello,

Thanks for the reply.  'Command Not-Found' is what the terminal returns.  I tried to add the nvidia driver from 'Add/Remove Programs', logoff/logout, with no change.

---

### Post by jaywatkins on 2007-11-22
I was able to turn on the restricted-drivers, and install/activate the nvidia driver.  Now, the screen resolution is 640x480 instead of 800x600!  I looked over my xorg.conf to see if there was anything amiss, but it looks fine.

Any ideas?

my xorg.conf =================================================

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV36 [GeForce FX 5700LE]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"DELL P780"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV36 [GeForce FX 5700LE]"
	Monitor		"DELL P780"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

===================================================

Thanks

---

### Post by Mountlake_Cut on 2007-11-23
This might help you. First backup your xorg.conf file then add two lines in
section ¨Monitor¨.

Your xorg.conf:

Section "Monitor"
Identifier "DELL P780"
Option "DPMS"
EndSection


add your montior&#347; HorizSync & VertRefresh rates here:

Section "Monitor"
	Identifier	"ViewSonic E6"
	Option		"DPMS"
        HorizSync 30-65
        VertRefresh 50-100
EndSection


You should google search your Dell P780&#347; HorizSync and VertRefresh rates for the correct numbers, I posted my Viewsonic E655 monitor section  as an example.
I  had to manually add those two lines to get my Nvidia TNT/TNT2 video card to work.  
Hope it works for you!

---

### Post by jaywatkins on 2007-11-23
I cannot edit the file now!  This is rather frustrating, XP/Vista can pick-up my video card.

Entering 'sudo nano /etc/X11/xorg.conf' or 'sudo gedit /etc/X11/xorg.conf' produces no result, just a carriage return.

The same happens when I try to set the root password with 'sudo passwd root', just a carriage return.  Executing 'passwd root' produces a kick-back response denying me access.

Any ideas?  Time for a reinstall?

---

### Post by Pumalite on 2007-11-23
Check in the Nvidia site what driver is appropriate for your card.

---

### Post by Mountlake_Cut on 2007-11-24
If it was me, I would just reinstall Gutsy again. After the install, make sure to back up your
original xorg.conf file before you do anything else.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup

then edit xorg.conf

sudo gedit /etc/X11/xorg.conf

save and restart the computer.

---

