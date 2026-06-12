---
title: "Edgy doesn't boot with idebus=66"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by muriloq on 2006-10-31
I've installed (from scratch) Xubuntu 6.10 (Edgy Eft). The following message appears at dmesg:

ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

The same occurred with Dapper (kernel 2.6.15-27); I've fixed it adding the kernel parameter idebus=66. However, if I do this in Edgy the system doesn't boot, simply freezes. 

The BIOS report that my disks works at 66MHz (the slowest one; the others are running at 100MHz). hdparm also lists them as using udma. 

Any ideas ? 

Thanks a lot in advance.

---

### Post by muriloq on 2006-11-01
A friend sent me this message, explaining it's not an issue at all:

> 
You almost certainly *don't* want to do that. idebus is the speed of your PCI bus, which is probably 33 MHz.  That's kinda a confusingly named option -- lots of people seem to think it has something to do with ATA/33 vs ATA/66 vs ATA/100, but it doesn't. See drivers/ide/ide.c....

Unless you're running a box with 66MHz/64bit PCI slots (doubtful) then overriding the pci bus speed will either crash you or at least do nothing at all. The PCI bus operates indepenantly of your FSB (front side bus) for your CPU and of your RAM i/o.


---

