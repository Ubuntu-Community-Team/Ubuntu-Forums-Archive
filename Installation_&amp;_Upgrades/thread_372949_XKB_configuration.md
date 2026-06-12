---
title: "XKB configuration"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2007-02-28
Got a problem when I log in, after trying to set up xbindkeys. Window shows with the following message:-


Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


I have ran the 2 proga above and get:-


gary@weldons-desktop:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "uk", "", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "uk", "", "lv3:ralt_switch"
gary@weldons-desktop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = 
 options = [lv3 lv3:ralt_switch,altwin  altwin:super_win]
 overrideSettings = true


I would be grateful if anyone out there could offer a solution :-k

---

### Post by celticbhoy on 2007-03-11
Bump !!!

---

### Post by zorkerz on 2007-03-14
same here with feisty
its very hard for me to type qwerty on a dvorak keyboard

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

