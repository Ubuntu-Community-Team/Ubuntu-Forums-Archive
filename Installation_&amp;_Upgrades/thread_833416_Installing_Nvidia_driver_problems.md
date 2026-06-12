---
title: "Installing Nvidia driver problems"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by tsayonara on 2008-06-18
Okay I installed Xubuntu tonight and am now trying to install Nvidia Drivers.

I got the driver, a .run file

1) Nvidia tells me to:
"sh NVIDIA-Linux-x86-96.43.05-pkg1.run"
**System tells me "nahh, only root can do that"**

2) Website told me, use"
"sudo sh NVIDIA-Linux-x86-96.43.05-pkg1.run"
**System tells me "nah dude, X is still running"**

3) Nvidia tells me to do something with booting with a something something 3 

I'm getting p'ssed off here :D!

Please tell me what to do

---

### Post by sisco311 on 2008-06-18
Install the driver from Applications --> System --> Hardware Drivers(or Restricted Drivers).

---

### Post by 505 on 2008-06-18
Or install EnvyNG which will automatically download the latest version of the drivers from Nvidia and install it.

---

### Post by tsayonara on 2008-06-18
Thank you for the fast replies.

I installed EnvyNG but how do I start it?

---

### Post by sisco311 on 2008-06-18
from a terminal:
```
envyng -t
```for text mode.
If you installed envyng-gtk:
```
envyng-gtk
```or
```
envyng -g
```

---

### Post by tsayonara on 2008-06-19
The driver installed succesfully but I don't know if the graphics card is properly working.

**Everything** I do takes forever to load, which I assume is not the intention even if I'm running on just the onboard driver.

In "hardware drivers" the driver still says 'not in use'

**Also:**

1) The window "Network settings" keeps freezing up

2) Sometimes suddenly I can't type any text

and 

3) Sometimes when I type it repeats one letter over and over for about a minute 

:(

---

### Post by PmDematagoda on 2008-06-19
Post the outputs of:-
```
cat /etc/X11/xorg.conf
```
and
```
cat ~/.xsession-errors
```

---

### Post by tsayonara on 2008-06-19
*As attachment*

I **can** open the Nvidia X window

Off-topic: When I connect to a secured wireless signal I can only choose WPE while my signal is WPA secured, what's up with that?

---

### Post by PmDematagoda on 2008-06-19
Open the xorg.conf file for editing with:-
```
gksudo gedit /etc/X11/xorg.conf
```
and edit the file to make it look like this:-
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"UseDisplayDevice"	"DFP"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

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
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Module"
	Load		"glx"
EndSection

```
save the file and then restart the X-Server by pressing Ctrl+Alt+BackSpace and see if that fixes things.

---

### Post by tsayonara on 2008-06-19
If I type that first line of code in the terminal nothing happens, it breaks to the next line

If I browse to and edit the file in Mousepad, when I save I get "can't open file to write"

So I can't edit :S?

---

### Post by sisco311 on 2008-06-19
> **tsayonara said:**
> If I type that first line of code in the terminal nothing happens, it breaks to the next line

If I browse to and edit the file in Mousepad, when I save I get "can't open file to write"

So I can't edit :S?

The default text editor in xubuntu is mousepad.
Type
```
gksu mousepad /etc/X11/xorg.conf
```in the terminal to edit the file.

---

### Post by tsayonara on 2008-06-19
Adjusted it but still got the weird problems.

Thanks to everybody for helping me but that was the final straw, I'll just install XP again..

---

