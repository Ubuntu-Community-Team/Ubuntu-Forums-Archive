---
title: "[help]X won't start after upgrade"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by angelo.yu on 2006-06-06
I upgraded breezy to dapper yesterday, after restarted my computer, Xwindow won't start.
Here are the errors in the Xorg.0.log:
```
(EE) Failed to load module "kbd" (module does not exist, 0)

(EE) Failed to load module "mouse" (module does not exist, 0)

(EE) Failed to load module "synaptics" (module does not exist, 0)

(EE) No Input driver matching `kbd'

(EE) No Input driver matching `mouse'

(EE) No Input driver matching `synaptics'
```

seems to say the input devices can not be loaded.
why do these error occur?
btw: I am sure the modules for kbd, mouse are in /usr/lib/xorg/modules/input.

Here is my Xorg.conf:

> Section "InputDevice"
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

---

### Post by angelo.yu on 2006-06-16
anybody could help?

---

### Post by starNIX on 2006-06-17
Exact same problem here...

Plz Help....

---

### Post by rcarring on 2006-06-17
Reinstall xserver-xorg

```

sudo apt-get install xserver-xorg

```

Once this package and dependencies has been installed, you can reconfigure xorg.conf by running dpkg --reconfigure xserver-xorg as root

```

sudo su -
(password)
dpkg --reconfigure xserver-xorg

```

Then once you are done, you can reinstall synaptic.

Make sure that when you boot, you hit Esc at the grubloader stage, picking the recover mode option, and then you won't be thrown into the gui by default.

In which case you will log in as root and not need to use sudo.

---

### Post by starNIX on 2006-06-17
That doesn't work....

It is complaining that the kbd module doesnt exist.
                                                    
[RIGHT]       
[/RIGHT]

---

### Post by DrSwing on 2006-08-17
I'm having the same problem.  Here are some other errors from the log file - 

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").

Everything worked fine in "Breezy" before the upgrade.

---

### Post by tseliot on 2006-08-17
Try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

if that doesn't work have a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

---

