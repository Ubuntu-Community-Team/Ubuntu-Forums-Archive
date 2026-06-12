---
title: "Desktop Effects 8.10 beta"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sesquipedalianman on 2008-10-10
I installed Kubuntu 8.10 on my HP 6730b laptop w/ a Intel 4500MHD video card.  Initially everything worked great including all the eye candy effects.  about 6 hours into using it I've started experiencing regular crashes of X that bring me back to the kdm login prompt.  The only way I've found to solve it is to turn off all desktop effects.  Any ideas in how to fix this or where the problem may lie?  Other than that I get full 1600x1050 resolution that looks great.

---

### Post by myddewji13 on 2008-10-10
Same problem on an ubuntu 8.10 hp pavilion 2407ca laptop... i think its compiz but besides that no idea..

---

### Post by inportb on 2008-10-10
If you're running KDE4, you should not be using Compiz :)

---

### Post by Eversmann on 2008-10-10
That's not really true. You can use compiz fusion on KDE4 (in fact, one of the latests updates are for kwin...)

That may be any other problem related to that. I'm on kubuntu 8.10 beta right now but not using compiz fusion at the moment. I'll try it when i have the chance and see how it's going.

---

### Post by sesquipedalianman on 2008-10-10
I didn't install anything specifically for effects, just whatever comes w/ KDE4 (kwin?).  I've read some things that may point to a video driver issue, but I'm still digging.

---

### Post by sesquipedalianman on 2008-10-16
Looks like this bug is reported in launchpad & is upstream in the x world.

[https://bugs.launchpad.net/xorg-server/+bug/282855](https://bugs.launchpad.net/xorg-server/+bug/282855)

---

