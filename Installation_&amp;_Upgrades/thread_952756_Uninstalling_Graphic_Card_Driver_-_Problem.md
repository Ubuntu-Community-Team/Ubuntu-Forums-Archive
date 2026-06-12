---
title: "Uninstalling Graphic Card Driver - Problem"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by Whiski24 on 2008-10-19
Hello everyone,

I am a complete noob and beginner at ubuntu, just so you know. Anyway I was surfing the internet and saw a site about how to install a driver for your grapic/video card. I saw that i had to press Alt-F2 and type 
  gksu displayconfig-gtk

Thats what i did and i checked if there was a driver already installed and there wasn't. (I have a ATI Radeon VR100 V7000 32MB??something like that) I did not find the right driver for my card so i installed a different one for some stupid reason! I have no clue XD. 
Now my screen only has the possible resolutions of 640 480, 600 400, or lower. I need 1024 780<??? Thats what it was before...

So i basically need to find out how to uninstall the video card driver!

Thanx all in advance...

---

### Post by robert shearer on 2008-10-19
> **Whiski24 said:**
> Hello everyone,

I am a complete noob and beginner at ubuntu, just so you know. Anyway I was surfing the internet and saw a site about how to install a driver for your grapic/video card. I saw that i had to press Alt-F2 and type 
  gksu displayconfig-gtk

Thats what i did and i checked if there was a driver already installed and there wasn't. (I have a ATI Radeon VR100 V7000 32MB??something like that) I did not find the right driver for my card so i installed a different one for some stupid reason! I have no clue XD. 
Now my screen only has the possible resolutions of 640 480, 600 400, or lower. I need 1024 780<??? Thats what it was before...

So i basically need to find out how to uninstall the video card driver!

Thanx all in advance...

You want to install the package  'envyng' from the repositories.

System=>Admin=>Synaptic package manager.

When this opens use the search option and type in envyng.

When the package is found right click on it and choose 'Mark for installation'.

Once it installs look in Applications=>System tools=>Envyng.

This package automates installing and uninstalling ATI/Nvidia drivers.

See this link for details...[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Whiski24 on 2008-10-20
Hey,

Thanx a lot, however it did not work completely... Now all i can do is stay at 800 x 600 which is OK  but I really love it if someone could help

Thanx a lot.

---

### Post by jerome1232 on 2008-10-20
Can you post your xorg.conf? How did you install your driver initially from the restricted driver manager?

```
cat /etc/X11/xorg.conf
```

---

### Post by Whiski24 on 2008-10-20
this is my xorg.conf 

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"3Dlabs Oxygen GMX"
	Busid		"PCI:1:0:0"
	Driver		"glint"
	Screen	0
	Vendorname	"3Dlabs"
	Option		"SWcursor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

```

as for 

> How did you install your driver initially from the restricted driver manager?

no idea what your talking about... i might not have mentioned but i started used ubuntu 3 days ago.

Thanx anyway

---

### Post by jerome1232 on 2008-10-20
Try deleting those mode lines and see if it helps

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck  # making a backup before we screw with it
gksu gedit /etc/X11/xorg.conf
```

try copy pasting this in, I basically removed anything that specified your resolutions

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"3Dlabs Oxygen GMX"
	Busid		"PCI:1:0:0"
	Driver		"glint"
	Screen	0
	Vendorname	"3Dlabs"
	Option		"SWcursor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

If the worst happens and you end up with a messed up display hit ctrl+alt+f1 to get a text based login, login then restore your backed up copy (might want to write this down in case)
```
sudo cp /etc/X11/xorg.conf.bck /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```


hope that helps

---

### Post by Whiski24 on 2008-10-20
Nothing Happened, except that xorg.conf stayed the way you changed it to but the highest resolution is still 800 600

Please Help 
Thanx

---

### Post by jerome1232 on 2008-10-20
Ok try this xorg.conf




```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"3Dlabs Oxygen GMX"
	Busid		"PCI:1:0:0"
	Driver		"glint"
	Screen	0
	Vendorname	"3Dlabs"
	Option		"SWcursor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024     780
		Modes		"1024x780@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

---

