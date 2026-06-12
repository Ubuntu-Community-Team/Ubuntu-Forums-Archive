---
title: "Yet Another NVIDIA Problem"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Eric Christenson on 2011-04-28
I happily ran Xubuntu 10.10 on my AMD Phenom II x6 CPU and ASRock 880GM/LE mobo for two months, with 8 Gigs of RAM.  It has on-board ATI Radeon graphics.  I bought an NVIDIA Galaxy GEFORCE GTX440 for the PCI-E slot, more for it's CUDA(compute coprocessing -- see [www.mersenne.org](www.mersenne.org)) capability than for the graphics; it is the largest such card the power supply in my system will support.

I enabled the Nvidia driver through the "enable drivers" screen, and got the usual boot into command prompt only after a brief meerkat silhouette. Holding down shift gets me into recovery mode, the mobo graphics stuff works fine. I'm ready to follow the NVIDIA instructions and get the latest drivers from Ubuntu-x-swat PPA.  

The NVIDIA instructions, of course, assume you only have NVIDIA cards in your system, but lspci has no trouble telling me I have two VGA compatible cards in my system.  
My questions are:
1) Is there an example /etc/conf/xorg.conf file that would let me run both the NVIDIA card and the on-motherboard ATI Radeon graphics?
2) At what point do I stop with the configuration if I decide I only want to run CUDA (graphics coprocessor running programming, not actually creating video) on the NVIDIA card, and no video?

Thanks

---

