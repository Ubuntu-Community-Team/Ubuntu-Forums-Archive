---
title: "Live CD dies with blank screen"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by batkins on 2006-07-07
I'm trying to install Dapper on my desktop machine - a homebuilt AMD64 with a Radeon 9250SE video card.

The installer boots and reaches the service-loading screen.  It seems to have no problems until it loads GDM and then "HP Printing Services".  At this point, the screen goes blank and nothing further happens.

I've tried all kinds of approaches to fixing this.  I've tried the alternate CD, tried both the i386 and amd64 CD's (in the desktop and the alternate editions).  I've tried passing noapic and nolapic to the kernel (as suggested on ubuntu-users); tried passing debian-installer/framebuffer=false to the kernel.

Nothing has helped.  The Ubuntu wiki indicates that my video card is fully supported by Dapper.  I had no problems installing Breezy a few months ago, the CD consistency checks all pass, and I was able to use one of the four CD's I've burned to install Dapper on my laptop without any problems.

How can I get this to work?

Bill

---

