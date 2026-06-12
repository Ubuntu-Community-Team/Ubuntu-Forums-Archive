---
title: "keyboard inbtrepid kde"
date: 2008-08-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LucasLinard on 2008-08-18
HI,
I've installed kubuntu 8.10 alpha 4 and my keyboard have several keys not working.
No arrows, no enter (numpad) no home, del, pd up or down, do slash.
can anyone helP (sorry no question mark either):confused:

---

### Post by mblakele on 2008-08-18
I have the same problem on an nc6400. Here's a workaround:

$ setxkbmap -model evdev

I have to do this each time I restart KDE4. I tried to build it into my /etc/X11/xorg.conf - but without success:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        #Option         "XkbModel"      "pc105"
        Option          "XkbModel"      "evdev"
        Option          "XkbLayout"     "us"
EndSection

Even with XkbModel set, my arrow keys, page keys, etc don't work until I open konsole and run "setxkbmap -model evdev".

---

