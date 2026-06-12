---
title: "Which Ubuntu server can I install on Supermicro P4SCE (Pentium 4)"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by reginald3 on 2014-05-02
I have an old Pentium 4 (!) Supermicro webserver. I'm not sure about the exact model but it has a P4SCE motherboard:

Key Features


1. Intel® Pentium® 4 Support up to 3.4 GHz, Celeron® up to 2.4 GHz (mine is P4, not Celereon)
2. Intel® E7210 (Canterwood ES) Chipset
3. Up to 4GB DDR 400/333/266 SDRAM (mine has 2 x 512 MB = 1 GB RAM)
4. 2 x Intel® 82541 Gigabit Ethernet Controllers
5. Serial ATA Controller on-chip (Intel® ICH5R)
6. 5 x 32-bit 33 MHz PCI (5V)
7. ATI RageXL 8MB PCI Graphic Controller

[http://www.supermicro.com/products/motherboard/P4/E7210/P4SCE.cfm](http://www.supermicro.com/products/motherboard/P4/E7210/P4SCE.cfm)

I'm wondering which Ubuntu version I can install? Would that be Ubuntu 8.04.4 LTS (Hardy Heron)?
[http://old-releases.ubuntu.com/releases/hardy/](http://old-releases.ubuntu.com/releases/hardy/)

---

### Post by mörgæs on 2014-05-02
If you want a server version (that is, no GUI) the standard 14.04 is the best choice.

---

### Post by reginald3 on 2014-05-02
Oh, your reply comes as quite a surprise to me. I was under the impression such old hardware needed an old Ubuntu version.

I'll try 14.04 then. That would heve to be the Intel x86 image, right?

Many thanks!

---

### Post by mörgæs on 2014-05-02
If you have 1 GB of memory you should use x86, also if your processor is 64 bit.

---

