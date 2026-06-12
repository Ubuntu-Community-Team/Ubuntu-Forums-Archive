---
title: "Usplash"
date: 2009-05-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2009-05-01
My boot splash goes into text mode, dmesg says
"usplash[850] general protection ip:b7f10d3b sp:bfc90bd8 error:0 in libusplash.so.0[b7efd000+29000])
Anybody know what this means or how to fix it ?
Thank, Cecil

---

### Post by Slug71 on 2009-05-01
> **cecilpierce said:**
> My boot splash goes into text mode, dmesg says
"usplash[850] general protection ip:b7f10d3b sp:bfc90bd8 error:0 in libusplash.so.0[b7efd000+29000])
Anybody know what this means or how to fix it ?
Thank, Cecil

Dont worry about it, Plymouth should be here soon. :P

---

### Post by autocrosser on 2009-05-01
Usplash has not been updated to work with the new kernel---as Slug said "don't worry about it"---I too am looking forward to Plymouth, although I will not be seeing all the "goodness" due to nVidia dragging their feet :(:(

---

### Post by Kevbert on 2009-05-02
There's a SIGSEGV [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/350250") with usplash as well. Hopefully we won't need to worry about that either!

---

