---
title: "Sessions Preferences missing tab"
date: 2008-07-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-07-27
I can't remember what the tab was called but it listed some stuff running and allowed you to stop them.

To use an example: I use Avant Window Navigator and don't have any Gnome Panels. I used the Sessions Preferences to end gnome-panels without it restarting. But now I can't do this, and have a Gnome Panel which I don't want. If I end it's process, it just restarts.

---

### Post by aamukahvi on 2008-07-27
Have you tried:
```
gnome-panel --sm-disable &
killall gnome-panel
```
Just a hunch and I don't know what it actually does. If you feel brave then go for it.
See "gnome-panel --help-all" for all the options.

Also see gconf keys in /desktop/gnome/session (gnome-panel listed as required component).

---

### Post by phenest on 2008-07-27
Doesn't work as it keeps restarting.

So why is the tab missing?

---

