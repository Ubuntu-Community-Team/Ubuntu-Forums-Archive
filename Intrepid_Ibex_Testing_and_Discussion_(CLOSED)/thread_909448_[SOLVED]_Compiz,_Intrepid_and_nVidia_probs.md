---
title: "[SOLVED] Compiz, Intrepid and nVidia probs"
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubername on 2008-09-03
Hi all,

I am trying to get compiz to work on my Intrepid install on a USB drive (the USB bit is a red herring: I have just upgraded my ubuntu HDD partition to Intrepid and have similar problems, but it is the USB drive I want to fix first before messing with the HDD.)

I can get it working with 'compiz --replace' but it only lasts as long as I have the terminal window open in which I typed that command.

I would really like to get under the hood a bit more about how compiz, xorg and drivers work together, as I have often seen the 'Xgl not present' and 'no drivers whitelisted'' messgaes when using 'compiz --replace'. I have hacked an old copy of xorg.cong as follows:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Option 		"AutoAddDevices" "off"
  	screen 		"Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

Note that the AutoAddDevices line is something I added in response to a previous problem ([http://ubuntuforums.org/showthread.php?t=880363](http://ubuntuforums.org/showthread.php?t=880363))

Also I have a Del 1908FP monitor (at least, that is what NVIDIA x server settings tells me) and I would like my xorg.conf to be optimised for that.

Any clues how I can make compiz 'sticky' and where I can find out more about the relationships between compiz and xorg? I am not sure that I have installed my nVidia driver correctly as I have done it from synaptic whereas on previous versions of ubuntu I used the 'restricted drivers' icon that popped up after install.

TIA

---

### Post by ubername on 2008-09-06
solved by [http://ubuntuforums.org/showthread.php?t=909550](http://ubuntuforums.org/showthread.php?t=909550)

---

