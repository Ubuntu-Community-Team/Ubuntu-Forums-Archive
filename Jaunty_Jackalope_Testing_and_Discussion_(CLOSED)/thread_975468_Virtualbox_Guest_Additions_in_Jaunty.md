---
title: "Virtualbox Guest Additions in Jaunty?"
date: 2008-11-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by InfinityCircuit on 2008-11-08
Hi, does anyone have mouse integration working with Virtualbox 2.0.4 in Jaunty?

I have installed virtualbox-ose-guest-utils.  If you don't do anything after this, it doesn't do anything special.  If you run /usr/share/virtualbox/x11config.pl, then when you start up X, mouse integration works--but the pointer can't be moved.  It can be clicked, but the pointer slowly moves to the lower right hand corner of the screen.  This means that I can click, but it just opens a million instances of the trash can.

I suspect this has to do with the new HAL autodetection.

Any ideas?

---

### Post by bash on 2008-11-08
Nope doesn't work for me either. Actually it neither works for Intrepid running in Virtualbox.

---

### Post by InfinityCircuit on 2008-11-18
Something in the recent set of updates has fixed this problem.

---

