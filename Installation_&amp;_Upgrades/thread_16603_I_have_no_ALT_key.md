---
title: "I have no ALT key"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by nazg on 2005-02-22
My ALT key doesn't seem to work after installing warty.
I mean, i can go to the console mode using Ctrl+ALT+F#, but if i want to type this: '[' or ']' or '@' i have to search from somewhere else and copy paste it.

Here's my xfree86 related part:


Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pt"
        Option          "XkbVariant"    "pt"


Help please ...

---

