---
title: "Update seems to have stopped Xorg talking to mouse and keyboard in Multiseat"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by obrouni on 2009-03-02
I'm using fully up to date Jaunty (28/2/09) configured with MDM ([http://wiki.c3sl.ufpr.br/multiseat/index.php/Mdm](http://wiki.c3sl.ufpr.br/multiseat/index.php/Mdm))

A update this week, between Monday and about Wednesday/Thursday seems to have made the underlying X server Display:0 stop receiving input events from the mouse and the keyboard.

The nested Xephyr sessions (Displays :1 to :4) running on top of Display:0 still work fine. This proves that the keyboards and mice are still being detected and passing events through to the Xephyr sessions correctly.

This regression or change in behaviour was first noticed by the fact that xorg goes into power saving due to inactivity and then cannot be woken up. Its also seen by the fact you can't change VT's anymore and keyboard LED's don't work.

I have a bug logged, but just wondering if anybody could help me troubleshoot this.

---

### Post by nyarnon on 2009-03-02
Probably a stupid question but did you try to reconfigure in save mode and through dpkg?

---

### Post by Martje_001 on 2009-03-02
What hardware do you use? I wonder this because I can't get multiseat to work at all..

---

### Post by Cracauer on 2009-03-02
> **Martje_001 said:**
> What hardware do you use? I wonder this because I can't get multiseat to work at all..

If you are using the binary NVidia drivers, those are documented not to do multiseat.

---

### Post by Martje_001 on 2009-03-02
I have tried radeonhd and ati (radeon / ati). No joy yet with xserver 1.6.

---

