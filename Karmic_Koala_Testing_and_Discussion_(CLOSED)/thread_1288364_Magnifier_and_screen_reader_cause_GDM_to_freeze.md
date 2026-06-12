---
title: "Magnifier and screen reader cause GDM to freeze"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jrothwell97 on 2009-10-11
I've been having some trouble with the new GDM, namely, when testing the accessibility features.

Magnifier and the screen reader will cause GDM to freeze: the system is still running, but X appears to have frozen, I can't move the cursor, and I can't alt-fx away to a tty.

I suspect this should be pretty easy to fix by editing a configuration file, probably a gconf key. However, to do that, I need to know:

[LIST]
[*]which file it is that I need to change
[*]where this file is
[*]what line I need to change, and to which value
[/LIST]

Any help would be greatly appreciated.

---

### Post by jrothwell97 on 2009-10-11
OK, I've managed to fix the problem... it turns out that when the new GDM starts, it runs all the launchers in /usr/share/gdm/autostart/LoginWindow. If you encounter this problem, simply move the offending launchers out of the way using a Live CD or Recovery Mode, and reboot.

---

