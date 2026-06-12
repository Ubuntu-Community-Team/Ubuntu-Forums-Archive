---
title: "[SOLVED] DPKG-RECONFIGURE Xserver-Xorg -- configuring mouse: TWO THUMBS UP!"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by perixx on 2008-01-28
**I don't know - should I cry or laugh?!?** :lol:
```
sudo dpkg-reconfigure xserver-xorg
``` needs to know 'how the mouse is connected': 
PS/2 - USB - yes, BUS-mouse (very common)... then comes this:
> choose mouse-connection:
/dev/input/mice
/dev/psaux
/dev/ttyS0
/dev/gpmdata ](*,)
That's just what every average-and-below user is excited about to to see! Applause !! =D>

perixx

---

### Post by perixx on 2008-01-30
After using the command and configuring the mouse, the mousewheel wouldn't work anymore.
I've solved the problem in the meantime:

> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "**[COLOR="Blue"]Im[/COLOR]**PS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
 
**[COLOR="Blue"]"Protocol" has to be 'ImPS/2' instead of just 'PS/2'! [/COLOR]**

> "Device" "/dev/psaux" was  "/dev/input/mice" initially, but seems to work fine nonetheless. > Option          "Emulate3Buttons"       "true" wasn't there before, but seems not to do any harm.

perixx

---

