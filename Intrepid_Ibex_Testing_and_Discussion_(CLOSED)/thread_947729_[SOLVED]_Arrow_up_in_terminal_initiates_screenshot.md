---
title: "[SOLVED] Arrow up in terminal initiates screenshot"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by OffHand on 2008-10-14
Hi guys,

After updating to Ibex the arrow up button if used in the Terminal does not cycle through the bash history but initiates a screenshot.

Help is greatly appreciated!

---

### Post by MaX on 2008-10-14
Check your compiz bindings


Or even better... rename your xorg.conf and start again.
It might be evdev and thus you must go into Keyboard & Settings and choose default for stuff
to start working again.

---

### Post by OffHand on 2008-10-14
> **MaX said:**
> Check your compiz bindings


Or even better... rename your xorg.conf and start again.
It might be evdev and thus you must go into Keyboard & Settings and choose default for stuff
to start working again.
Anywhere particular? Screenshot is disabled in Compiz.

---

### Post by OffHand on 2008-10-14
> **MaX said:**
> Check your compiz bindings


Or even better... rename your xorg.conf and start again.
It might be evdev and thus you must go into Keyboard & Settings and choose default for stuff
to start working again.

xorg.conf is fine
```
Section "InputDevice"
	Identifier     "Generic Keyboard"
	Driver         "kbd"
	Option         "CoreKeyboard"
	Option         "XkbRules" "xorg"
	Option         "XkbModel" "pc105"
	Option         "XkbLayout" "us"
EndSection

```
Keyboard and Settings under Preferences looks good too (Generic 105 - USA) 
Actually my whole keyboard layout seems to be messed up. Does anyone know where the config file is?

Any other ideas?

---

### Post by OffHand on 2008-10-14
Al of the sudden it started working again after a reboot!

Note: It happened for several days and rebooted plenty of times.

Thanks for your help though  :)

---

