---
title: "Radeon X300 Screen Flicker When Opening Programs"
date: 2008-07-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BwackNinja on 2008-07-08
I upgraded to Intrepid from Hardy (on a separate partition, and not by accident) and was able to upgrade all packages. However, when opening up any application, the screen freezes and flickers for a second before opening it (this includes tray icons like fusion-icon), and the following is added to Xorg.0.log:

```
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Found color CRT connected to primary DAC
in RADEONProbeOutputModes
(II) RADEON(0): Adding Screen mode: 1360x768
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 2
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
```

I achieve my 1360x768 resolution with a modeline, though this problem is present without it. It is especially bad when logging in, where a lot of programs are starting up at once. I have no other graphics problems, and compiz-fusion runs fine as usual. The problem is there whether I'm using compiz-fusion or metacity.

I'm wondering if anyone has or had this problem or just why it happens. In hardy I have it only when starting compiz and whenever I start an app in wine.

---

### Post by erkiha on 2008-07-08
Hi,

I have exactly the same problem when using external monitor on my laptop (with intel i945GM video card). 

Also in Hardy it flickered only with wine, in intrepid with every program opening.

---

### Post by RAOF on 2008-07-08
It looks like X is doing monitor-detection each time you open a program.  This will result in the screen flashing that you describe.  It also seems totally unnecessary.

Have you filed a bug?  If both of you are seeing this problem with Intel & ATI cards I'd suggest that the xorg-server source package is a good place to file it against.

---

### Post by erkiha on 2008-07-09
Filed a bug 246836

---

