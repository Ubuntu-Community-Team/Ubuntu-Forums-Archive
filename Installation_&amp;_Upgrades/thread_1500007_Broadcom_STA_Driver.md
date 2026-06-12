---
title: "Broadcom STA Driver"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by Prototypes on 2010-06-02
How do I install the Broadcom STA Driver without an Internet connection in ubuntu?

---

### Post by efflandt on 2010-06-03
Insert the install CD for your Ubuntu version.

Open Synaptic and under Settings > Repositories check the box to add CD to the repository.  Not sure if you need to hit the swirling arrow to Reload (ignore unavailable internet sources).  You could install bcmwl-kernel-source if you want to, but I think that will automatically install when you activate it below.  Close Synaptic (so following can work).

Go to System > Administration > Hardware Drivers and Activate Broadcom STA.  Exit that and eject CD.

Once wireless is configured and working, go back to Synaptic, uncheck the CD from the repositories, then hit swirling arrow to Reload internet sources, and wait for Quick Search to finish sorting.  Done.

---

