---
title: "Kernel feeze on boot at libata version 1.20 loaded at install"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by new299 on 2007-01-03
Hi,

I'm trying to install Ubuntu 6.10 (AMD 64 version) on a new Dell Optiplex 740, this a AMD 64x2 system. When booting the kernel it feezes at: "libata version 1.20 loaded." The last few lines are:

ohci_hcd 0000:00:0b.0: OHCI Host Controller
ochi_hcd 0000:99:0b.0: new USB bus registered, assigned busnumber 1
SCSI subsystem initialized
libata version 1.20 loaded

Knoppix boots well, I've also tried removing the graphics card and using the onboard graphics (no difference).  I have also tried added noacpi to the boot options, which made no difference again. I have also tried the normal and alternative installation CDs.

The system contains:

ATI x1300 ATI Radeon graphics card
250Gb SATA HD
2Gb DDR2 Memory
Nvidia chipset motherboard (I can dig out specific version if required)

Any help appreciated!

---

### Post by new299 on 2007-01-03
setting apci=off seems to have resolved this

---

