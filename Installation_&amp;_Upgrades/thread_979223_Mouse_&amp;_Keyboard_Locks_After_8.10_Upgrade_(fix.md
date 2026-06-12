---
title: "Mouse &amp; Keyboard Locks After 8.10 Upgrade (fixed)"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by rvickers on 2008-11-11
I've seen several threads on this issue so I'm posting my resolution.

Boot to Recovery Consol and go to a command prompt.
Nano /etc/X11/xorg.conf
Add the following:

Section "InputDevice"
        Identifier       "Configured Mouse"
        Driver           "Mouse"
        Option           "CorePointer"
EndSection

Section "InputDevice"
        Identifier       "Generic Keyboard"
        Driver           "kbd"
        Option           "XkbRules" "xorg"
        Option           "XkbModel" "pc105"
        Option           "XkbLayout"  "us"
EndSection

Ctrl O to save
Ctrl X to exit

Hope this helps someone...:)

---

