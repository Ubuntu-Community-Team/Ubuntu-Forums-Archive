---
title: "New installation; unreadable screen"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by jimtobias on 2005-10-19
I just installed 5.10 on an AMD64 system with an ATI Radeon 9200 DVI; the monitor is a Dell 2005FPW, DVI connected.  After the text screen is finished, an unreadable screen comes up; it's mostly blue with short horizontal grey line segments all over it.  There's some black at the top.  Keyboard and mouse are useless.  Any ideas?

---

### Post by chanders on 2005-10-20
I suspect it is your ATI driver... Try replacing the driver with 'vesa' in xorg.conf....

If your screen comes up then the driver is to blame.... You may also want to try 'radeon'....

---

