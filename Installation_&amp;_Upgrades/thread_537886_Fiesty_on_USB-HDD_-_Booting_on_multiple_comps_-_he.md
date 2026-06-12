---
title: "Fiesty on USB-HDD - Booting on multiple comps - help pls"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by marx2k on 2007-08-29
I have installed (and am running) Fiesty from an external USB 120G HDD.

It works great on this laptop which has an ATI video card.  No problems at all.  In fact, when I move it over to my other laptop also (unfortunately) with an ATI card, again no glitches.

However, if I try running Ubuntu from the external USB HDD on a computer with an nVidia or Intel video card, X doesn't start and I have to manually reconfigure X to load the modules for those cards.  It's doable but a real annoyance, especially since it defeats the purpose (quick, easy bootup on any computer).

Is there a method (like the LiveCD seems to do) that will auto-set the correct drivers on bootup for any computer I choose to boot it on?

Any help would be much appreciated!

---

### Post by marx2k on 2007-08-29
I will try asking another way...

How about a way to do it that when it's booting, it checks to see whether the system its booting on uses ATI or NVidia and then provides the correct xorg.conf before starting to load X and if the system doesn't use either one, it begins a root-access of dpkg-reconfigure on xserver-xorg.

Anyone?

---

