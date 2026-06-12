---
title: "Can't make superkey assignment permanent in Xubuntu 14.04"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2014-10-18
Using a standard US 105 microsoft 600 keyboard on Xubuntu 14.04. Edited the **/etc/default/keyboard** file and assigned the superkey to the left windows key (lwin).

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS="composer:lwin"

Then logged out & in and the **xorg.0.log** did not register the change (see attached file). Then, I tried using **xorg.conf** to load up the options and this didn't work either.

Option         "xkb_rules" "evdev"
Option         "xkb_model" "pc105"
Option         "xkb_layout" "us"
Option         "xkb_options" "composer:lwin"

However, the keyboard setting in the Setttings manager correctly identifies the Left Win key as the superkey, and if I type in the terminal **setxkbmap -option compose:lwin** then the superkey works for the duration of the session. **setxkbmap -print -verbose 10** produces the following report

Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     us
options:    compose:lwin
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us+inet(evdev)+compose(lwin)
geometry:   pc(pc105)
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us+inet(evdev)+compose(lwin)"	};
	xkb_geometry  { include "pc(pc105)"	};
};

What am I doing wrong?

---

### Post by TheFu on 2014-10-19
Waited a day to respond, since I'm not running Xubuntu. However, in LXDE, the key mappings are controled by the WM config file ... . ~/.config/openbox/lxde-rc.xml
There are examples inside it, modify to your hearts desire and they stay.  LXDE uses openbox for the WM.  What does XFCE4 use? That's the file to be altered, perhaps?

---

### Post by ineuw on 2014-10-19
> **TheFu said:**
> Waited a day to respond, since I'm not running Xubuntu. However, in LXDE, the key mappings are controled by the WM config file ... . ~/.config/openbox/lxde-rc.xml
There are examples inside it, modify to your hearts desire and they stay.  LXDE uses openbox for the WM.  What does XFCE4 use? That's the file to be altered, perhaps?

Thanks for your reply. I found the answer. First, the xfce4 keyboard layout is in **/home/user/.config/xfce4/xfconf/xfce-perchannel-xml/keyboard-layout.xml**. This resolved the mystery of where it stores the superkey info displayed in the Settings manager keyboard options.

In the same folder, I found the **xfce4-keyboard-shortcuts.xml** which stores the list of possible shortcuts, which in my case most of the the assignments are empty as in: 
<property name="&lt;Super&gt;w" type="empty"/>

To be cautious, I will not mark this post "resolved" until I tested it. :-)

---

