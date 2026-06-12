---
title: "[SOLVED] hardy livecd doesn't see harddrives but systemrescuecd does"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by delfick on 2008-07-28
hello

I have a slight problem where I accidently uninstalled much of the basic packages in my system (was trying to uninstall my lamp server using tasksel and it got a bit carried away)

now I can't connect to the internet from my computer (using my laptop now) and when I put in the ubuntu hardy cd and use apt-cdrom add, to add the cdrom, i still can't install packages from it.

so I can't do a simple sudo apt-get install ubuntu-desktop
(tells me it has no installation candidate)

So I've come to the conclusion that I should just reinstall ubuntu (most of my configuration is on my home partition (which is seperate to the linux partition) so reinstalling ubuntu shouldn't cause too much trouble for me.

The problem i have is that the ubuntu live cd can't see my harddrives and so I can't install ubuntu using the livecd.

However the systemRescue cd can see my harddrives.

So I'm wondering if it is possible to somehow install ubuntu from within the systemrescue cd.

(I've had a look at debootstrap but that looks very much beyond my skills)

Thankyou very much for help.

---

### Post by delfick on 2008-07-30
dw, got the internet working again and did "sudo apt-get install ubuntu-desktop"

problem solved :)

---

