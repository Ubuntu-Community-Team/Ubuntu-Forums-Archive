---
title: "Keyboard problems"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by cOlav on 2006-06-23
Manage too fix higher resolution in 
dpkg-reconfigure xserver-xorg
After finishing this my Norwegian keybord failed. And when I tryed too change it 
inn System- preference- keyboard I got this error message:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Anyone who can answer this? I vould like to get my norwegian letters back. Thanks.

---

### Post by XAsmodeanX on 2006-06-23
[http://http://ubuntuforums.org/showthread.php?t=70388&highlight=reinstall+xkb]("http://http://ubuntuforums.org/showthread.php?t=70388&highlight=reinstall+xkb")

Read on down to the fourth post.

---

