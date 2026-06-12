---
title: "Karmic - no ttys!"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fela on 2009-08-16
I installed ubuntu karmic today in a separate partition - mostly it works OK, apart from the main problem: the ttys are gone and they're replaced with a blinking, useless cursor. Also, the splash (xsplash?) is a low/funny resolution even with the vga=868 (1440x900) that worked in jaunty. Any tips?

thanks.

---

### Post by lessgov2007 on 2009-08-16
> **fela said:**
> I installed ubuntu karmic today in a separate partition - mostly it works OK, apart from the main problem: the ttys are gone and they're replaced with a blinking, useless cursor. Also, the splash (xsplash?) is a low/funny resolution even with the vga=868 (1440x900) that worked in jaunty. Any tips?

thanks.
I have not used Karmic. Look under /etc/event.d/ folders and you should see files similar to tty1, tty2, tty3, tty4, etc. Look into 1,2,3,etc, and check to see if there commented out or something. I dunno if this is it, but worth looking into.

---

### Post by fela on 2009-08-17
> **lessgov2007 said:**
> I have not used Karmic. Look under /etc/event.d/ folders and you should see files similar to tty1, tty2, tty3, tty4, etc. Look into 1,2,3,etc, and check to see if there commented out or something. I dunno if this is it, but worth looking into.

Thanks - but there are no folders under that name in karmic! :lolflag:

Luckily I kept all my stable 8.10 installation safe on my other drive (on an LVM setup aswell :P).

---

