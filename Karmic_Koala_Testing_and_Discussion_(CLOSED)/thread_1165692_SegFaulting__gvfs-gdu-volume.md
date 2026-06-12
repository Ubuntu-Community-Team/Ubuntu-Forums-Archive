---
title: "SegFaulting  gvfs-gdu-volume"
date: 2009-05-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-05-20
G'day folks :)

I'm getting repeated segfaults like this:

May 21 12:17:54 PPP kernel: [   46.705920] gvfs-gdu-volume[4330]: segfault at 18 ip 00007f2f4ccce2f1 sp 00007fffdf874600 error 4 in libgdu.so.0.0.0[7f2f4ccc3000+22000]

Any thoughts?

---

### Post by ronacc on 2009-05-20
I noticed the same thing in my logs .

---

### Post by manuelb on 2009-05-21
I've the same problem that manifested itself just after the upgrade to Karmic: also, when connecting to the machine via a FreeNX client the GUI is messy and old-gtk styled, i don't know if that's related in some way but trying to switch to another theme i got gvfs segfaulting, not every time btw.
Also note that loading the theme manager presents all the themes, borders, colors, etc.. with just a question mark, but ~/.themes DOES contain everything as before upgrading.
Anyone with a similar thing?

---

### Post by taavikko on 2009-05-21
[https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/376145](https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/376145)

---

### Post by Nullack on 2009-05-21
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/376145](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/376145)

---

