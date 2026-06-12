---
title: "Mouse (etc.) issues with OLD kernel in 6.06"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by madscientist on 2006-06-06
Hi all;

I have to use an older kernel on my system (specifically, the kernel from Red Hat Enterprise Linux 4 which is a 2.6.9-based kernel with lots of Red Hat patches).  This is because we use ClearCase at work and they have a binary-only kernel loadable module for their special filesystem (MVFS) and they only support RH and Suse.

I had this working with Ubuntu 5.10 with no problems: everything worked (at least, as well as things worked in 5.10: my major problem there was that Evolution 2.4 had a number of bugs in the Exchange Connector, and I have to use Exchange at work for calendaring).

Last night I upgraded to Ubuntu 6.06, but kept my special 2.6.9 kernel.  I ran into four problems I wonder if anyone can help me with:

 a) My network driver isn't loaded automatically.  I have a Dell Dimension 3000 desktop.  I fixed this by hand by adding the e100 KLM to /etc/modules so this is not a big problem.

 b) PCMCIA fails to start.  I don't care about this either, but thought I'd mention it.

 c) Sound doesn't seem to work: the sound KLMs seem to be loaded.  Actually, maybe the soundcard driver itself is not loaded, like the ethernet driver.  I'll have to look into that.  This is not much of a problem since it's a work system, however I do like to listen to tunes during intense hacking sessions so it would be nice to fix.

 d) The is the biggest problem I _must_ fix.  My mouse behaves "badly".  First, the sensitivity is WAY up; the slightest touch sends it across the screen.  I managed to use the mouse config dialog to turn it down a lot and now it's a bit more usable.  But the other issue is that scrolling no longer works!  The scroller button still works as mouse3, but the scrolling of windows (mouse4 and mouse5) doesn't do anything at all.  I really need this!

The thing is, if I boot into the standard Ubuntu kernel (2.6.15) it all works fine... BUT I can't do any work since I can't use ClearCase.  So, it must be an issue with the older kernel and new Ubuntu, which I know is a nonstandard installation, but I have to resolve this (esp. (d)) or else drop back to Ubuntu 5.10.

Help???

---

