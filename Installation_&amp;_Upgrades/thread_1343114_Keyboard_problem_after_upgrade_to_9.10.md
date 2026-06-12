---
title: "Keyboard problem after upgrade to 9.10"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by Sunca sin on 2009-12-01
Hello, 



I have upgraded from 9.04 to 9.10 and everything went OK. I have only one problem with keyboard. If I have NumLock on, I can't use keys  (Insert, Home, Delete, End, Page Up, Page Down and arrows), but if I turn it off then they work, but then I can't use numbers on Numpad.


 xorg.conf                                                    \etc\default\console-setup

 
Section "InputDevice"                                      XKBMODEL="pc105"
    # generated from default                            XKBLAYOUT="si"
    Identifier     "Keyboard0"                             XKBVARIANT=""
    Driver         "kbd"                                           XKBOPTIONS=""
EndSection




Any ideas?

---

### Post by Z652 on 2009-12-01
Is it a PS/2 keyboard, mine was and everything worked okay when I switched to a usb keyboard.

---

