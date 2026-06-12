---
title: "ATI dri2 issues Karmic"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tretle on 2009-09-20
I am currently running a Dell Inspiron 6400 which uses the ATI Mobility X1400 graphics card. On fedora 11, the last stable release which came roughly the same time as Jaunty I had full dri2/kms support. 
I am now running an up to date version of karmic and I can still not use dri2 or kms with my card. 
What the hell?
I was told that its switched off by default but when I switch it on the screen goes black on startup and when I do get it running some hours later it falls back to mesa.
Anyone any info on this? Anyone experiencing the same dri2 issues with ATI cards?

---

### Post by ELD on 2009-09-20
DRI had major bugs (caused me and many others gdm to fall into a loop) and it has been disabled for karmic, Jaunty did not have it so it is no step backwards.

See bug 419126 in launchpad.

---

