---
title: "CPU problem after 9.10 upgrade"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by mathspeedy on 2010-03-26
Hi! Today, I decided to upgrade my Dell Studio 17 to ubuntu 9.10 (a bit late I know).
But after the upgrade, I noticed the laptop was a bit noisy, and saw that the CPU was 100% used and the laptop was actually IDLE.
Does someone here, experienced this problem before?
Any help would be appreciated.

--
Posted from my iTouch.

---

### Post by efflandt on 2010-03-27
I wonder if it has anything to do with something in your xorg.conf, because X changed, and by default 9.10 does not even have xorg.conf.

I installed 64-bit 9.10 from scratch on a new Dell 1545 without issues (only needed Broadcom STA).  Even though comments on Best Buy version said it got hot around the mousepad, that one only got mildly warm in Win7 or Ubuntu, and fan only ran when necessary.  But I believe Studio versions have different video card/chip.

---

### Post by dimoftheyard on 2010-03-27
Can you tell us which program actually uses the CPU? Also, are any other programs running? Firefox + XServer sometimes caused one (or both) of them to use up the CPU, but I don't know whether this problem still exists.

---

### Post by mathspeedy on 2010-03-27
Hi!, I found what was eating the CPU so much! 
It was "Gnome-Do", I just killed the process and Tadaa!:p

P.S: Take a look at the attachement...
Oh, and by the way does anyone knows how to change the Shutdown... button look, like in 9.04?

---

