---
title: "EEPC1000H compiz ?"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xens on 2009-07-30
Hi there, since two weeks I can't activate compiz. I thought I had to wait some compiz or intel driver updates but I'm still stucked.

#glxinfo | grep direct
direct rendering = yes

Intel 945GME inside.

Any hints? Thanks, Romain :KS

---

### Post by b3n87 on 2009-07-30
I know there were a few problems with some of the Intel graphics drivers, so maybe its a bug thats in the process or being fixed?

---

### Post by OmarAvelar on 2009-07-31
Using the configuration edtitor (gconf-editor) navigate to:
 ```
desktop/gnome/session/required_components"
```then right click the "windowmanager" key and hit "Set as Default"... and restart your gnome session. :)

---

