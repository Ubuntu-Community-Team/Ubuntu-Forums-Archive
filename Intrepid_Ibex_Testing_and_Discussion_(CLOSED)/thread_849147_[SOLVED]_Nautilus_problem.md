---
title: "[SOLVED] Nautilus problem"
date: 2008-07-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chrismine on 2008-07-04
After yesterday's updates Nautilus is not working. It flashes a few times on screen.  Here is the output from terminal: chrisjan@ubuntu:~$ nautilus seahorse nautilus module initialized Initializing nautilus-share extension  ** (nautilus:6105): WARNING **: Unable to add monitor: Not supported Segmentation fault  Does somebody else have this problem, is there a possible fix?  Thank you.

---

### Post by mgsfan on 2008-07-04
mine opens up whenever I click on desktop icons or inside a folder...lol so I'm hoping an update fixes that soon

---

### Post by Nullack on 2008-07-04
Its fixed now, no more segfault in nautilus when I run it

---

### Post by ronacc on 2008-07-04
from the terminal try    sudo aptitude update     and when that  completes    sudo aptitude safe-upgrade    then reboot.

---

### Post by chrismine on 2008-07-04
> **ronacc said:**
> from the terminal try    sudo aptitude update     and when that  completes    sudo aptitude safe-upgrade    then reboot.

 ronacc you are brilliant. It worked! Thanks.

---

### Post by Benjamin_Lebsanft on 2008-07-04
> **ronacc said:**
> from the terminal try    sudo aptitude update     and when that  completes    sudo aptitude safe-upgrade    then reboot.
alt+f2 and 'killall nautilus' should do the same and save you some time :)

---

### Post by yomellamozov on 2008-07-04
Hi.
Since few weeks ago, I've been using the "sudo nautilus" to install new fonts. Last Monday I tried to do the same, I typed on the Terminal "sudo nautilus" but the nautilus didn't load, it just stood this way:

> oscar@oscar-laptop:~$ sudo nautilus
Initializing nautilus-image-converter extension
Initializing nautilus-share extension
seahorse nautilus module initialized


Please, help

---

### Post by Gina on 2008-07-04
With graphical apps like nautilus it's best to use **gksudo** (or **gksu** which is the same) rather than **sudo**.  I'm not saying that is your problem but it's one possibility.

---

