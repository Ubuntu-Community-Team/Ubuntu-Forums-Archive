---
title: "[SOLVED] How to fix blank screen/no signal with NVidia (e,0,0x827d)"
date: 2014-05-19
forum: Installation &amp; Upgrades
---

### Post by xyz4 on 2014-05-19
Hello all,

after a long journey of google and forums I finally triggered out, what lead to that mysterious errorcode.
With all standard NVidia drivers, i had this error as last message in the Xorg.0.log and some freezing CPU's stuck atr 100%, system not reacting any more.

The main hint was, to step forward to NVidia driver 331. With that one, the error code got translated and speaking now: "Failed to initialize DMA"! Whoohoo, that's finally something to deal with!!!

To solve this, I had to deactivate IOMMU in my motherboards BIOS. The reason was potentially, that this used the same space as the DMA wanted to have, so it didn'T work.

As i struggled several days and quite a dozen of hours now, I thought it's a good idea, to provide this knowledge to the community somewhere, so here it is!

Best regards
QD

---

### Post by mörgæs on 2014-05-19
Thanks for an attempt at marking the thread 'solved'. Better though to use Thread Tools.

---

