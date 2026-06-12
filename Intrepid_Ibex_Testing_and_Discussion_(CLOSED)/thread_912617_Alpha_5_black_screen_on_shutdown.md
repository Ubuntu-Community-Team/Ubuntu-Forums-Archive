---
title: "Alpha 5 black screen on shutdown"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by swimb on 2008-09-06
I tried running the alpha 5 live cd on my older PIII system with 8.04 on it. On the desktop all the icons are just boxes with x's in them, I tried to shutdown but cant read the menus, there is no readable text there and more boxes with x's. I clicked one of the boxes and Im at a black screen with only the mouse cursor. How can I shut it down properly?

---

### Post by ronacc on 2008-09-06
alt+F1 should give you a terminal , log in to it then sudo halt

---

### Post by swimb on 2008-09-06
alt+F1 does nothing, all i have is a black screen and a mouse cursor.

---

### Post by ronacc on 2008-09-07
then try alt+F2 , alt+F3  if still no term try ctrl+alt+bkspc if still nothing ctrl+alt+del if nothing then you will have to shutdown with the pwr button or main sw .

---

### Post by swimb on 2008-09-07
Thanks, ctl+alt+bkspc got me to a screen where it says 

EXT3-fs error (device sda1): ext3_find_entry: reading directory #4759553 offset 0

from there alt+F1 gets a command line but i cant login, more fs errors.
This was my first time with an alpha, Ill wait for the beta and give it another try. Thanks for the help!

---

### Post by ronacc on 2008-09-07
the live cds have been flaky all the way through ibex .

---

