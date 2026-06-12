---
title: "Live CD failure and Alternative Install both present same graphical oddities"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by exosyst on 2006-10-30
Here&#8217;s a problem i&#8217;ve yet to see anywhere else:
On loading the live CD, it loads right up to the point where the gnome splash should appear&#8230; then it shows a distorted graphical glitch instead of the splash - then the audio plays but no commands work at all (no CTRL Alt+F1) and it hangs (except for the mouse).

I then tried the alternate install CD, this worked ok however it refused to install to the MBR on my SATA drive. I decided to use the CD to &#8216;Boot first harddisc&#8217; &#8212; surprise, up it boots&#8230; up comes GDM, still functional F keys with tty etc, switching back to the GDM and logging in then presents the same graphical errors and hangs.

The distortion and errors (followed by lockup) appears on the GDM as soon as you click Session>Choose Session.

Strange!

Specs:
SATA Disc Primary
SATA Disc secondary
IDE Master (installed ubuntu to this one and then changed BIOS so it was first boot device)
IDE slave

Nvidia 7800GTX, 1GB RAM, AMD 3800XP with ASUS deluxe mobo with nvidia nforce4 chipset

Quite bothersome as I've managed to install it on my laptops with no problems at all, can anyone replicate or am I one in a million :-k

---

### Post by exosyst on 2006-11-01
Fixed it - seems to have been a problem with the nv driver. I changed it to VESA and it's all working now.

---

