---
title: "Console mode graphics issue with nVidia"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Dysphoria on 2009-10-10
After the last bunch of updates I tried to enter console mode (ctrl-alt-F2) but the screen is messed up (just a lot of green lines). I can return to my desktop (ctrl-alt-F7) just fine but the terminal mode is unreadable.

Tried re-installing the nVidia 185 driver I'm using but that didn't help.

Anyone else has this problem or know how to fix it?

---

### Post by sgage on 2009-10-11
I have the exact same problem. It also occurs when I put my computer to sleep - before it closes down, the same video corruption.

No idea of a fix, alas.

---

### Post by cyberkilla on 2009-10-11
I got this whenever I tried to change the resolution of the console. If I left the mode alone, it worked fine.

---

### Post by bertand on 2009-10-11
option vga=791

---

### Post by FuturePilot on 2009-10-11
Known bug [https://bugs.launchpad.net/ubuntu/+bug/447692]("https://bugs.launchpad.net/ubuntu/+bug/447692")

---

### Post by trulan on 2009-10-11
This problem occurs regardless of which video driver is selected.  I would think that this will be dealt with fairly quickly.

FWIW, the consoles are functional - you just can't see what you are doing. ;)

---

