---
title: "Help. Stuck at Boot."
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2010-07-19
I posted this on this furum, but over at Ubuntu "Server Platforms", but didn't even get a response.  I fifgure this was probly more of an install problem (maybe why I didn't get aresponse there) so I'm asking here:> **MAFoElffen said:**
> I tried installing Ubuntu LTS 10.04 Server Edition 64 bit on one of my drives today...

The install completed fine until it went to reboot. Then it faills while initializing the graphics. It tries (a purple flash on the screen) then goes to a text based dump on the monitor.

Ubuntu LTS 10.04 Desktop Edition run great on this machine. I'm wondering if the Server Edition confused by multiple instances of a video card? This computer is SLI bridged:

```
ASUS A8N32-SLI Deluxe Gaming Edition
AMD 64 FX-60
4GB PC3200 Performance Gaming RAM
Two XFX GeForce 6800GT Ultra SLI bridged video cards
1TB SATA drive
250GB SATA drive
500GB IDE drive
```Is the xorg or whatever video subsystem that the server edition uses different than Desktop Edition?
If you've been following me in other posts, this is a multi-boot machine.  Is has Win7 64bit and Ubuntu LTS 10.04 Desktop 64bit on the 1TB, Windows Vista 64bit and OpenSolaris on the 250GB and trying to Install Ubuntu LTS 10.04 Server Edition 64bit on the 500GB along side a separate swap partition and a data partition.

* On the install process, I have the SATA drives unmounted.

The reason I mentioned "xorg" is that back in January-February, I ran into some upstream xorg problems between OpenSolaris and Solaris 10, where OpenSolaris had updated there xorg version,  That lost their compatibitlity with multiple instances of the same video card (where SLI "is").  That's where I had to got to a dev version of OpenSolaris, that went to an even newer version of xorg, that fixed that.

Is the graphical logo/login screen in Ubuntu in the server edition after the init of xorg?
If so, is the xorg of the Server Edition different than the Desktop Edition?

---

### Post by lisati on 2010-07-19
Thread closed, duplicate of [http://ubuntuforums.org/showthread.php?t=1533941](http://ubuntuforums.org/showthread.php?t=1533941)

This forum is used by volunteers. Perhaps the person who can help you has not seen your other thread yet.

---

