---
title: "infinite cycling with xsplash"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by godhika on 2009-09-15
After I scewed my karmic install, I tried to install it completley new with the daily build which caused an infinite cycling after the xsplash (I hear the first few bits of the startup sound, then xsplash starts again and again and again......). Tried a install with alpha 3, after the update the same issue. This is a DellStudio 15 laptop with a ATI graphic card. Anyone an idea?

---

### Post by jmmL on 2009-09-15
Might well be related to [http://ubuntuforums.org/showthread.php?t=1265224](http://ubuntuforums.org/showthread.php?t=1265224)

Apparently upgrades to libc6 are still coming through (and might not be mirrored yet if you're using one) so I'm holding off upgrading for a few more hours.

---

### Post by x33a on 2009-09-15
remove splash from the kernel parameters.

this will boot the system without the splash screen and you'll be able to see at what point the system hangs.

---

### Post by godhika on 2009-09-15
Hmmm- I don't think so. All thoses cases are related to nvida graphic cards, and, since I have xsplash, which means also the xserver - which is also not the case in there. So I guss it must be omething different

---

### Post by uBeer on 2009-09-15
This could work:

[http://ubuntuforums.org/showthread.php?t=1255442&highlight=ati+karmic&page=2&post=11](http://ubuntuforums.org/showthread.php?t=1255442&highlight=ati+karmic&page=2&post=11)

I have a Studio 17 with ati. I now have radeon drivers working, but not the ati or the fglrx.

---

### Post by godhika on 2009-09-15
thanks -that helped. Now I only have to find out why my network aint working on that machine - oh the joys of alpha testing ;)

---

