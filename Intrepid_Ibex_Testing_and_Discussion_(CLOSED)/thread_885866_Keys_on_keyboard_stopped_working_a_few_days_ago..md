---
title: "Keys on keyboard stopped working a few days ago."
date: 2008-08-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MaX on 2008-08-10
A few days ago my keyboard in Gnome started acting weird.

I can't write At signs (neither with AltGr or Ctrl+Alt) or press the Home, End,Insert, Delete.
Page Up and Page Down doesn't behave as expected and the arrow keys doesn't work.

I've tried reseting the layout but nothing works.

in Xfce the keyboard behaves as expected.

---

### Post by klange on 2008-08-10
There was a switch in keyboard drivers to evdev, so whatever your keyboard layout was set to is now incorrect and you should instead use "evdev Managed Keyboard". (That's worked for most everyone so far)

---

### Post by neltnerb on 2008-09-10
Thanks, this fixed my issues as well.

---

