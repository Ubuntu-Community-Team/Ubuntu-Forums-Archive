---
title: "Why xorg.conf  does not contain keyboard layout ???"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-07-19
I have updated this morning, then an old bug show-up, I had use 

ORIGINAL:
Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "CoreKeyboard"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
EndSection

CORRECTED:
Section "InputDevice"
        Identifier "Generic Keyboard"
        Driver "kbd"
        Option "CoreKeyboard"
        Option "XkbRules" "xorg"
        Option "XkbModel" "pc105"
        Option "XkbLayout" "us,ru"
        Option "XkbVariant" ",winkeys"
        Option "XkbOptions" "grp:ctrl_shift_toggle,grp_led:scroll"
EndSection

but my xorg.conf does not contain it.

---

### Post by ajgreeny on 2008-07-19
New xorg 7.3 is much changed from previous versions and xorg.conf is nearly empty.  But what is your problem exactly and what is it on your keyboard that is not working properly?  If it works OK don't worry about the conf file, it really doesn't matter any more.

---

### Post by hoboy on 2008-07-19
The problem is that each times I close the computer my keyboard change back to some a setting that I think is us.
I am using danish keyboard setting, so I have to manually set back to danish keyboard setting always.

---

### Post by ajgreeny on 2008-07-19
Try changing the layout in System>>Preferences>>Keyboard.  That should do it.

---

### Post by killerwhale65 on 2008-07-27
Hello,

I have the same problem. Changing the layout via setting only works for the current session. Upon reboot it changes back to the for me wrong layout.

---

