---
title: "Karmic Koala freeze problems"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by ebenuk on 2009-12-15
Hi,
I've just upgraded to 9.10 and various dialog boxes seem to freeze/hang.

Eclipse stopped working on me but I found a thread that recommended setting

export GDK_NATIVE_WINDOWS=true

which got that working. However, when using gimp for instance to open a file the machine hangs. Any pointers please?

Thanks a lot!
Ewan

---

### Post by xifer on 2009-12-15
> **ebenuk said:**
> Hi,
I've just upgraded to 9.10 and various dialog boxes seem to freeze/hang.

Eclipse stopped working on me but I found a thread that recommended setting

export GDK_NATIVE_WINDOWS=true

which got that working. However, when using gimp for instance to open a file the machine hangs. Any pointers please?

Thanks a lot!
Ewan

first up have top running in a terminal window and check it when system appears to hang.  If nothing much is going on then first guess might be window manager/compositing crash so what should be running and has anything crashed?
Try running a problem app from another terminal window to get more info. 


HTH

---

### Post by ebenuk on 2009-12-15
Thanks, well the first thing I found is that trackerd was hogging the CPU. I&#472;e just been out for four hours and trackerd is still taking all it can get. Is that normal on a 36GB drive?
Ewan

---

### Post by xifer on 2009-12-16
> **ebenuk said:**
> Thanks, well the first thing I found is that trackerd was hogging the CPU. I&#472;e just been out for four hours and trackerd is still taking all it can get. Is that normal on a 36GB drive?
Ewan

Should not happen.  But I had that   problem after upgrading to U9.10 and it was fixed  by a later upgrade.  So I'd recommend taking latest updates using the update manager.

---

### Post by ashokgm on 2010-01-27
[http://linux-solution-for-us.blogspot.com/](http://linux-solution-for-us.blogspot.com/)

---

