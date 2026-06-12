---
title: "CRT Max Refresh Rate Unavailable in Alpha 4"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by floborg on 2009-08-18
I use a Compaq MV500 CRT monitor.  With Hard-Jaunty, my maximum refresh rate of [COLOR="Blue"]85[/COLOR] Hz was always available for the resolutions compatible with it (800x600 is what I use).  With the Karmic Alphas, the highest available is [COLOR="Red"]75[/COLOR] Hz.  I am writing this from the Aug 17th daily build.

This was never an issue with the monitor and Xorg, and I have used both Ubuntu and Puppy Linux with it using two different machines.  The first had onboard ATI Rage Pro LT graphics, and the current uses onboard Intel graphics.

Is this a known issue?

Here is the output of **lshw**:

```
*-display
     description: VGA compatible controller
     product: 82G33/G31 Express Integrated Graphics Controller
     vendor: Intel Corporation
     physical id: 2
     bus info: pci@0000:00:02.0
     version: 02
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap_list rom
     configuration: driver=i915 latency=0
     resources: irq:25 memory:fdf00000-fdf7ffff ioport:ff00(size=8) memory:d0000000-dfffffff(prefetchable) memory:fdb00000-fdbfffff

```

I'll post the output from my current (and properly-functioning) Jaunty install when I get a chance.

---

### Post by floborg on 2009-08-18
So, here's the output of **lshw** in my Jaunty install:

```
*-display UNCLAIMED
     description: VGA compatible controller
     product: 82G33/G31 Express Integrated Graphics Controller
     vendor: Intel Corporation
     physical id: 2
     bus info: pci@0000:00:02.0
     version: 02
     width: 32 bits
     clock: 33MHz
     capabilities: msi pm bus_master cap_list
     configuration: latency=0

```

By the way, **xrandr** in Karmic doesn't list the 85 Hz refresh rate, but it does in Jaunty.

---

### Post by floborg on 2009-09-06
Not a problem in Alpha 5.

---

