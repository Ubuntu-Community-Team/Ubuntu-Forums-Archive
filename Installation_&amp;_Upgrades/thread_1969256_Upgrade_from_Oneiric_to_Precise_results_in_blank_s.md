---
title: "Upgrade from Oneiric to Precise results in blank screen on mythfrontend."
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by whosmatt on 2012-04-29
Just upgraded today.  System boots normally and I see the flash of xfce desktop before mythfrontend starts, and then nothing.  The display is on, just blank.  VNC shows the same thing.  I searched and found a thread from last fall when Oneiric was released; the poster had the same issue... there was no resolution mentioned in the thread.

If I ssh in and kill mythfrontend, the desktop reappears (but then mythfrontend starts again).

If it helps, this is a Nvidia 7xxx system (7050, maybe).. the other thread references another thread where the ATI driver was a culprit or at least part of the problem.

Thanks,

Matt

---

### Post by whosmatt on 2012-04-30
I got help on another thread over in the mythbuntu forum.  It was a problem with OpenGL and mythfrontend.  In case somebody searches for this, switch the themepainter to qt and all will be well (though not as pretty).

-M

---

