---
title: "HDIO_SET_DMA failed: Operation not permitted"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by ulrich_e on 2008-04-30
After upgrading from 7.10 to 8.4 I get the message that dma is disabled for my ide harddisk and of course that slows down my system. Trying ~# *hdparm -d1 /dev/hda* just gives me 

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma     =  0 (off)

When I google on *HDIO_SET_DMA failed: Operation not permitted* the results suggest that modules for my chipset are not loaded. Using *lspci* to find out about my chipset I get the following result:

...
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
...

Does anybody have an idea which module should be loaded?

Thanks in advance, Ulrich

---

