---
title: "DVD / CD's  don't Unmount  when removed"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Glugglug on 2009-10-25
I have found the DVD icon  remains on the desktop after  the disk is removed   and even after  another disk is inserted .

It has to be manualy unmounted  before the new  DVD / CD will run 

the  places list  has both  the previous disk and the current disk listed at the same time. 

Is this happening on all installs or just mine  .


I'm using  9.10 RC  i386  desktop .

---

### Post by VMC on 2009-10-25
If you mean after you push the eject button on the front bezel of the DVD/CD, then yes I have the same problem. 

If I "eject" using the mouse then it works ok.

---

### Post by Glugglug on 2009-10-26
> **VMC said:**
> If you mean after you push the eject button on the front bezel of the DVD/CD, then yes I have the same problem. 

If I "eject" using the mouse then it works ok.

I hadn't noticed   how I was ejecting  the  cd   but yes  it works  when I use the mouse.

---

### Post by VMC on 2009-10-26
I found this launchpad bug #[448921]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/448921") report that describes the situation. Read it carefully. Several conditions, one of which is what your described. I checked it effects me too.

---

