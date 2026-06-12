---
title: "Held back packages broke fglrx"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jfbilodeau on 2009-10-14
Good day,

After doing my update of Karmic, the kernel images were held back. I didn't pay attention, and rebooted the machine after the update. Fglrx stopped working, and would crash the system (yeah, I know. It's crap, but it allows me to play games).

After doing apt-get install linux-generic linux-headers-generic linux-image-generic and a reboot, the problem was fixed.

J-F

---

### Post by DougieFresh4U on 2009-10-14
Curious as to why those packages were held back.
I updated 3 partitions this morning, one 32 bit and two 64 bit and all went very smooth.

---

### Post by ranch hand on 2009-10-14
I am wondering about that too.  I updated 4 32bit variations this morning and had the kernel updates held back on one of them.  It was a newer install too (beta).

---

### Post by Longinus00 on 2009-10-14
> **jfbilodeau said:**
> Good day,

After doing my update of Karmic, the kernel images were held back. I didn't pay attention, and rebooted the machine after the update. Fglrx stopped working, and would crash the system (yeah, I know. It's crap, but it allows me to play games).

After doing apt-get install linux-generic linux-headers-generic linux-image-generic and a reboot, the problem was fixed.

J-F

This is beause you need the headers to recomiple fglrx each time the kernel gets update. Without recompiling, the drivers aren't really going to work.

Packages can be held back for all sorts of reasons. In this case, probably because of some dependency issues.

---

