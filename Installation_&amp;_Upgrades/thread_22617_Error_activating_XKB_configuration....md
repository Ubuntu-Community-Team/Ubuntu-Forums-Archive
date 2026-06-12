---
title: "Error activating XKB configuration..."
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by FXWGBill on 2005-03-28
The whole error message is this:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>

The outputs of the two commands:

root@CrazyEccentric:/home/mreccentric # xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""
root@CrazyEccentric:/home/mreccentric # gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us]
 model = pc104
 overrideSettings = false
 options = []
root@CrazyEccentric:/home/mreccentric #


I see that one says 104 key keyboard and the other 101...  I guess that is causing a conflict.  I am just not sure what the easiest way to fix it is, and it's running too good to stumble around and poke at straws.

Any help would be appreciated...

Thanx, 

Bill

---

### Post by ubuntu-geek on 2005-03-28
Look in your /etc/X11/xorg.conf for this line..

Option "XkbRules"   "XFree86"

Replace to

Option "XkbRules"   "xorg"

That should fix it up.

---

### Post by FXWGBill on 2005-03-28
It already is...

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"


where is the 101 key keyboard parameter at?  Seems that is what needs to be changed...

Bill

---

