---
title: "Suspected Bug on Alpha 4 with USB support"
date: 2008-08-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aggelos.satanas on 2008-08-15
For some reason the when the GDM boots up I lose all usb support, keyboard and mouse both fail to work even though the wireless reciever (i've tried a wired keyboard and mouse too) registers the caps and num lock keys to be working, I can also boot into recovery mode through grub and use my keyboard there (I hade to fix x as there was also no screen, only sound). Anyone else have this bug and is it possible that I can fix it?

---

### Post by jalmargyyk on 2008-08-15
I wonder if this could be the same bug, that is in [this]("http://ubuntuforums.org/showthread.php?t=880363&highlight=mouse&page=2") thread. Take a look at the post #11 and add the lines to xorg.conf.

---

