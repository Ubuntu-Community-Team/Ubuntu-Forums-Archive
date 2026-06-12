---
title: "Print Screen from keyboard doesn't work!"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-03-28
Is it just me or is this a new err... *feature*?
Cheers, Mike

---

### Post by macstevejb on 2009-03-28
Working fine on my Labtec media keyboard along with all the  other media keys.

regards,

---

### Post by scaine on 2009-03-28
If you have compiz enabled, make sure that you have the gnome-compatibility plug-in enabled.  There's an open bug about that :
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328679](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328679)

---

### Post by Shabakthanai on 2009-04-13
It doesn't work on my computer.  64bit AMD Quad Jaunty Beta up to date.  What is a suitable alternative?  Thanks!:lolflag:

---

### Post by scaine on 2009-04-14
What doesn't work?  Your printscreen key?  Or printscreen functionality in general?

As for alternatives, there's an excellent print capture utility built into Compiz - just turn it on with CCSM, then choose what key binding you want to activate it with.  Hold that key down, then drag the area of screen you want to capture.

I find that it's very rare that you want to capture the whole screen, so this plug-in for compiz is a godsend.  It work exactly like the snipping tool built into Vista.

If you use gnome-do, there's a plug-in to activate printscreen for screen capture.  I haven't used it though.

Finally, I think there's a printscreen in Applications/Accessories.  If it's not there, turn it on using the menu editor (System/Preferences/Main menu)

If all else fails, then hit Alt-F2 (or start a terminal) and type "nome-screenshot --interactive".

Hope that helps.

---

