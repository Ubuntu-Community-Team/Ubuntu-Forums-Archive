---
title: "Swapping control and caps lock?"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by glaze on 2009-03-31
How can I swap control and caps lock in Jaunty? In Intrepid I have the following lines in my xorg.conf, but they don't work in Jaunty:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fi"
        Option          "XkbOptions"    "ctrl:swapcaps"
EndSection


```

---

### Post by Reb on 2009-04-01
What about System > Preferences > Keyboard > Layouts > Layout Options?

---

### Post by Reb on 2009-04-01
You can also make Caps Lock an additional Ctrl - because who really needs Caps Lock, anyway...

---

### Post by glaze on 2009-04-02
Thanks for the reply, but I'm using Xubuntu. I solved the problem by using xmodmap on the startup.

---

