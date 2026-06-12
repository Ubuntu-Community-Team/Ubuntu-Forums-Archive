---
title: "XKB error"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vaibhav on 2010-04-09
Hi,
I see the following error on startup:
```
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10706000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```
Result of last two commands mentioned there:
```
$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us", "", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us", "", "lv3:ralt_switch"
$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us,in	bolnagri]
 options = [lv3	lv3:ralt_switch,grp	grp:alt_shift_toggle]
 model = 
```
This error wasn't present earlier, but started occurring since a recent upgrade.

How do I resolve it?

Thanks.

---

