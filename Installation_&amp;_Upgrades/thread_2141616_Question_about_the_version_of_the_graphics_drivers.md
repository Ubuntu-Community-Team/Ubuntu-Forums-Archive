---
title: "Question about the version of the graphics drivers (13.04)"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by jkapsi on 2013-05-03
Hi

I'm using ubuntu 13.04 and when i go to abbout this computer, in the section graphics it says: Driver: VESA:M92

and when i type in terminal fglrxinfo the output is:

```

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500/5100 Series
OpenGL version string: 3.3.11672 Compatibility Profile Context

```

My question is: Which graphic driver my pc is using?

---

### Post by lovebluesky2009 on 2013-05-03
Advanced Micro Devices, Inc   is the manufacture

ATI Mobility Radeon HD 4500/5100 Series is your hardware

so I think the third line is your driver version, but I am not sure.

---

### Post by Mark Phelps on 2013-05-03
You will not be able to use the fglrx drivers with your card and any Ubuntu version newer than 12.04.1.  Starting with 12.04.2, Ubuntu upgraded their X-server version to a newer one that is no longer compatible with the fglrx drivers that work with the HD 2x/3x/4x-series cards.

---

