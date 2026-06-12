---
title: "Installing an ISDN card"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by choizy on 2006-07-14
I'm trying to install an ISDN card for the first time. Both my ethernet cards were found during installation but when i run ipconfig -a I don't see any ippp0 card. After checking the syslog I found this output:

Jul 14 19:44:48 Router kernel: [   38.551467] mISDNd: kernel daemon started
Jul 14 19:44:48 Router kernel: [   38.552720] mISDNd: test event done
Jul 14 19:44:48 Router kernel: [   38.568147] Winbond W6692 PCI driver Rev. 1.13
Jul 14 19:44:48 Router kernel: [   38.568275] PCI: Found IRQ 11 for device 0000:00:0c.0
Jul 14 19:44:48 Router kernel: [   38.568328] mISDN_w6692: found adapter Dynalink/AsusCom IS64PH at 0000:00:0c.0
Jul 14 19:44:48 Router kernel: [   38.568382] W6692: Winbond W6692 version (0): W6692 V00
Jul 14 19:44:48 Router kernel: [   38.626870] w6692: IRQ 11 count 4
Jul 14 19:44:48 Router kernel: [   38.626896] w6692 1 cards installed
Jul 14 19:44:48 Router kernel: [   38.641410] ISDN L1 driver version 1.11
Jul 14 19:44:48 Router kernel: [   38.747454] ISDN L2 driver version 1.20
**Jul 14 19:44:48 Router kernel: [   38.748111] mISDN: INTERNAL ERROR in drivers/isdn/misdn/stack.c:596**
Jul 14 19:44:48 Router kernel: [   38.748433] release_l1 id 1
Jul 14 19:44:48 Router kernel: [   38.748457] mISDNd: addr(f0000) prim(f1980) failed err(-92)
Jul 14 19:44:48 Router kernel: [   38.782502] CSLIP: code copyright 1989 Regents of the University of California
Jul 14 19:44:48 Router kernel: [   38.819327] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
Jul 14 19:44:48 Router kernel: [   38.936794] HiSax: Linux Driver for passive ISDN cards
Jul 14 19:44:48 Router kernel: [   38.936814] HiSax: Version 3.5 (module)
Jul 14 19:44:48 Router kernel: [   38.936827] HiSax: Layer1 Revision 2.46.2.5
Jul 14 19:44:48 Router kernel: [   38.936838] HiSax: Layer2 Revision 2.30.2.4
Jul 14 19:44:48 Router kernel: [   38.936849] HiSax: TeiMgr Revision 2.20.2.3
Jul 14 19:44:48 Router kernel: [   38.936860] HiSax: Layer3 Revision 2.22.2.3
Jul 14 19:44:48 Router kernel: [   38.936871] HiSax: LinkLayer Revision 2.59.2.4

The line in bold looks kinda bad to me.

Anny ideas? Please say if i need more information.

---

