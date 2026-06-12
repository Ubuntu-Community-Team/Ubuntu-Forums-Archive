---
title: "Upgraded and nothing but problems with fglrx"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by ppatalano on 2007-04-26
I have a FireGL v5200 graphics card. I was previously using edgy and had my card and driver installed beautifully, I was running xgl and Beryl without a flaw. 

My readout for fglrxinfo use to be very perfect as this
> peter@peter-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.6011 (8.28.8)

But now, nothing but trouble
> peter@peter-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)


This is what my card is recognized after the upgrade and installation of fglrx. Argh! :mad:

---

### Post by dlittle on 2007-05-01
I have the same issue.

---

### Post by ppatalano on 2007-05-01
And, it's still driving me up a wall.

---

