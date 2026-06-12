---
title: "VidMode not functional via Ctrl-Alt-KeyPad(+/-)"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by BBT on 2006-11-04
Screen resolution switching via Ctrl-Alt-KeyPad+ and Ctrl-Alt-KeyPad- does not work.

Installation is of Edgy on a clean harddrive. All configurations are as defaulted by installation.

The screen resolution DOES switch properly via the gvidm utility. This verifies that video drivers and the VidMode extension are operating correctly.

keyboard section of xorg.conf is:

```
Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbOptions" "lv3:ralt_switch"
EndSection
```

---

### Post by philippe_carlo on 2006-11-04
Doesn't the xorg file need to contain the correct modelines for that?
See:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by BBT on 2006-11-04
There are multiple, correctly configured mode lines. This is demonstrated by using the gvidm utility which allows me to select any video mode on the fly. All of that works fine. What does not work is keypad selection of the video modes. I believe the problem is keyboard handling related.

---

