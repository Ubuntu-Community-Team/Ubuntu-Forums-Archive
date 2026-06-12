---
title: "[SOLVED] The need for using modprobe floppy before mounting floppy"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alienexplorers on 2008-10-08
I am wondering if there is going to be a fix to the problem that when you first start your computer you need to enter sudo modprobe floppy.  After that first time I am able to mount and unmount the floppy drive without using the modprobe line.

---

### Post by alienexplorers on 2008-10-09
I really want to get this problem straightened out ASAP.

BUMP

---

### Post by MaX on 2008-10-09
You could probably put the floppy module in /etc/modules

I for one am glad that they don't load floppy support from the begining, I haven't used a floppy in the last 8 years.

---

