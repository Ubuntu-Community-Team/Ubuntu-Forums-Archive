---
title: "Ubuntu 10.10 EHCI booting problem"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by rdoganov on 2010-12-10
Hi,
 
I just installed Ubuntu 10.10 on an oldish laptop and it won't start. While loading it gets stuck at:
 
```
 
ehci 0000:00:03.3: USB 2.0 'Enhanced Host Controller' (EHCI) Driver
ehci 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
ehci 0000:00:03.3: EHCI Host Controller
ehci 0000:00:03.3: new USB bus registered assigned bus number 1
ehci 0000:00:03.3: irq 23, io mem 0xec004000

```
 
There is no problem when booting from the Live CD (except for having to use nomodeset, because of an ATI Radeon 9000 issue). 
 
Any help would be appreciated.

---

