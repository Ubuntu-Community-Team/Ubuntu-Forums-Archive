---
title: "[SOLVED] Unable to wake up after lock screen"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Philonimbus on 2008-10-16
Hi,

Each time I use the Lock Screen feature : Ctrl+Alt+L, the screen locks alright, but I can't go back to my session.

The login screen won't show up, no matter what key I press or how hard I move the mouse.

As it isn't a documented bug, I was wondering if I haven't done something wrong ?

---

### Post by Philonimbus on 2008-10-24
Ok, I found the answer on a french forum :

```
gconftool-2 -t string -s /apps/gnome-screensaver/lock_dialog_theme system
```

This command does the trick

---

