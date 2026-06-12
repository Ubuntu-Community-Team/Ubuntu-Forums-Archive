---
title: "How to install video card driver?"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by driggins on 2006-10-11
Greetings,

Linux and Ubunut newbie here.

I'm having trouble getting my xserver to behave. Autodetect apparently does not choose the proper video driver. When I force it to use "VGA" at 8-bits, I get video. Otherwise, I get errors.

I'm supposing I can find a more appropriate video driver on the net somewhere. Help here would be appreciated, too.

If I find a better fit, how do I install it?

My machine is an IBM NetVista 8311-XX7. The integrated video is Intel 845G.

Thanks,
daryl

---

### Post by shof2k on 2007-10-23
Edit your xorg.conf to use the i810 driver instead of the intel one.  I have an intel 845G graphics card and that worked for me.

---

