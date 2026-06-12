---
title: "How disable powernowd during install before full load?"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Necreia on 2007-10-04
I've had to do a reinstall of Ubuntu (hard drive full reformat), and I'm running into the same problem I had last time.

The issue is, I have a Core 2 Duo and Powernowd causes random freezes during install or using the O/S.  The solution is to disable it once the install disk fully loads, then install ubuntu, then remove powernowd. Last time it took 30-40 reboots and disk loads in order to get a time where I could get to a terminal and type the command to disable powernowd before the freeze, and I'd much like to avoid having to play that game again.

Is there a way to disable powernowd from loading from the disk at all for the install process?  Either blocking it from attempting to load, or do a step-by-step load and skip that particular app?

---

### Post by Necreia on 2007-10-04
Bump

---

### Post by tgalati4 on 2007-10-04
I assume that you disabled all power-saving features in the BIOS.  Also, set Plug-N-Play OS to  "NO"

Disable the parallel port and serial port (temporarily) to free up interrupts in case its an interrupt conflict.

---

### Post by Necreia on 2007-10-04
Interesting, I'll try those!  (No, I haven't turned off the power saving features).

Once powernowd is gone the O/S is rock solid for weeks runtime, it's just that step borks it.

---

