---
title: "Keyboard layout"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by bredelet on 2007-04-23
This is driving me crazy...

How do I tell Ubuntu to use the French AZERTY keyboard layout?

I ran dpkg-reconfigure xserver-xorg, I set the French layout in Preferences/Keyboard, to no avail.

X.org 70101000
_XKB_RULES_NAMES(STRING) = "xorg", "pc102", "fr", "intl", "lv3:ralt_switch"

layouts = []
model =
options = [lv3 lv3:ralt_switch,eurosign eurosign:e]
overrideSettings = true

Thanks!

---

### Post by lassegs on 2007-04-23
How about trying this:

```
sudo apt-get install console-common

kbd-config
```

---

### Post by bredelet on 2007-04-23
I solved that by running dpkg-reconfigure xserver-xorg again and clearing the keyboard options that it set by default (lv3 and intl).

---

