---
title: "Thinkpad T30 Startup"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by tufcamman on 2008-03-24
Hi, I recently installed 7.10 on my Thinkpad T30.  Everything is working great but for some reason it takes literally almost 10 min to start up.  After the BIOS does its thing and I select the OS the screen remains black for a very long time before coming to the boot screen.  Has anyone experienced this before?  Any ideas?

---

### Post by lcason on 2008-03-24
Assuming that it is not connected to a network (wired or wireless) that is scanning or doing something else weird, and if it is a clean install (no recompiled kernel with non-standard drivers), then it could be some kind of hardware issue.  I've run prior versions of Ubuntu on a T30 with no issues. I'd try booting some other OS (KNOPPIX or even Ubuntu) from a live CD and see if you get the same long delay. You may need to go into the BIOS setup to make the optical drive the first device in the boot order so that the machine will actually boot from CD rather than the HD.

---

### Post by tufcamman on 2008-03-25
It is a clean install from the ISO downloaded from Ubuntu.  It doesn't have the extremely long delay when booting to the Live CD.  Its not really a terribly big deal.  Just if anybody has come across this before.  Thanks!

---

### Post by YotoshiWii on 2008-03-25
Hey, i'm having the exact same problem, only i'm running on a T40. Ubuntu 7.04 worked awesome for me, but when i upgraded (clean install) to 7.10 I also have to watch the "Black Screen" for around ten minutes. Is there any know way to fix this problem?

But to be honest it dont bother me that much, Ubuntu could not run any smoother once it's up and running. xD

---

