---
title: "stops when loading scripts"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by dagamer on 2007-11-20
just for to start with 7.04 worked fine with this.

i ordered cds of 7.10 and just recieved them. When i go to load them it gets to the point after the ubuntu graphical loading screen and goes to the command line loading screen and says its running scrips from it. It gets that far and nothing happens.

i have done the checksum and it returned ok.

i am running with a
 msi v-class motherboard
2 gigs of ddr2 ram
and an amd athlon 64 x2 4000+ 2.1ghz

any suggestions help is greatly appreciated.

---

### Post by colo on 2007-11-20
Try booting the sytem without the "splash" and "quiet" kernel parameters; you may also need to supply "nosplash" on the kernel's command line to get verbose output. Somewhere, a more telling error message should hide.

---

