---
title: "Startup stalling at hotplug subsystem"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by TheEclypse on 2005-08-23
I have just managed to install Ubuntu on my Shuttle ST20G5 (AMD64 machine).  I am using the i386 version because of problems with having to recompile packages for 64bit.  Now, when the system is booting up, it gets to the point where it says:

"Starting hotplug subsystem"

and stays there, ive left it for a while and it never moved on from there.  I tested the keyboard and found the caps lock/scroll lock/num lock keys still responded to being pressed, so I am a bit confused.

I only have one USB device connected, and that is my Mitsumi 7-in-1 card reader.  When I get home i will try booting with it unplugged, and USB disabled in the bios.

Any ideas?

---

### Post by tonysathre on 2005-08-23
open synaptic and make sure hotplug is installed, it should be but if it aint install it

---

### Post by af92 on 2005-09-08
You could also try and make sure to unplug your USB device before you boot up and then reconnect it again after you get to boot screen.

-josh

---

