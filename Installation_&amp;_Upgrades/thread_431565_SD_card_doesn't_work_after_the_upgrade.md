---
title: "SD card doesn't work after the upgrade"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by diegor on 2007-05-03
Hi,

I had Ubuntu 6.06 AMD64bits in a Toshiba with core2duo and the multimedia card reader (SD cards, ...) worked fine with sd-cards.

I updated to Ubuntu 7.04 and no the sd-card reader does not work any more. I introduced the card in the slot but nothing happens, and it is not mounted.

with "lshw" I get the following information:

       *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: b.2
                bus info: pci@03:0b.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: iomemory:ffa05000-ffa05fff irq:23

Does anybody know what can I do?, thank you very much

---

