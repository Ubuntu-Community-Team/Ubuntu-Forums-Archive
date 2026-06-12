---
title: "Problem Changing Brightness"
date: 2008-08-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by niccholaspage on 2008-08-11
I just upgraded to Ubuntu 8.10 from 8.04.
Everything was fine except the keyboard,Which I fixed.I unplugged my laptop.This made my screen very dark so I used the brightness keys(FN+F6,FN+F7) And It didn't work.

Note:It worked great in Hardy Heron.

EDIT:My volume key does not work.I think it is because I selected the Evdev keyboard.
EDIT2:My brightness keys don't work,My volume thing doesn't work.I think it is because of the evdev keyboard.I had to set my keyboard to it.It was the same in Hardy and nothing wrong.

---

### Post by niccholaspage on 2008-08-13
Bump.
I really need to fix this.

---

### Post by RAOF on 2008-08-13
My keybord symbols changed recently; my volume, next, etc keys changed from some special keycode to XF86PlayPause, XF86VolumeUp, etc, and I needed to re-assign the various keyboard shortcuts in System->Preferences->Keyboard Shortcuts.  That won't fix your brightness keys, but they're handled by something else anyway - I'm pretty sure that's handled by your ACPI keys driver.

EDIT: For more information, see [here](https://wiki.ubuntu.com/IntrepidIbex/TechnicalOverview#Caveats)

---

### Post by niccholaspage on 2008-08-13
My fix right now is just to use the Brightness applet in the gnome panel and same for the volume.

---

