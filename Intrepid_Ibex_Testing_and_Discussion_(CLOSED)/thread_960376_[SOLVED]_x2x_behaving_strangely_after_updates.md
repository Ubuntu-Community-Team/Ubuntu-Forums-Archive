---
title: "[SOLVED] x2x behaving strangely after updates"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ndugu on 2008-10-27
I use x2x to share my keyboard/mouse between my laptop & desktop. Everything worked fine under 8.04, and everything had been working fine under 8.10 until the updates sometime between Friday 10/24/08 and Monday 10/27/08.  Now, when my mouse tries to leave the "to" screen, often times it gets confused and reenters the "to" screen instead of the "from" screen.  I have to move my mouse to the edge of the "to" screen several times to get it back onto the "from" screen.  Anyone else experiencing problems?

---

### Post by ndugu on 2008-10-27
I fixed this by manually running xrandr on my "from" computer with the correct monitor settings.  Even though the screens were correctly set up in gnome's Screen Resolution tool, the resolution settings didn't seem to carry over to everything correctly.

---

