---
title: "Keyboard Layout Problem"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by sepia-shots on 2007-10-21
Hi,

Just upgraded to 7.10 and everything seems cool so far except the keyboard layout, which has 1 (that I've found) minor issue in that I can't print a pound sign. No matter what I do I only manage to produce a 3 (the other shift characters are fine). I've tried changing the keyboard layout but get the following error:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

The results of the above give:

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "uk", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "uk", "", ""
$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = microsoft
 overrideSettings = true
 options = []

I'm using an MS natural keyboard (PS2). Any help greatly received!

Cheers

Pete

---

