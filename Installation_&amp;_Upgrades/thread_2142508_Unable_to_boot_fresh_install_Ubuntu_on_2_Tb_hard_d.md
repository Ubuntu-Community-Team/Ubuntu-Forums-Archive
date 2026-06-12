---
title: "Unable to boot fresh install Ubuntu on 2 Tb hard drive"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by overlord.gaurav on 2013-05-05
I just did a fresh install of 64-bit Ubuntu 13.04 from a USB stick on my 2 TB hard drive and it won't boot.
I had created a 490 GB parition for root ("/"), a 10 GB parition for swap area.

My computer specifications are: 

Intel i7 Processor
3 * 2 GB RAM
2 TB WD Hard Drive
Nvidia GeForce 450 GTS graphic card

---

### Post by overlord.gaurav on 2013-05-06
Problem solved.
A Wndows 8 copy of MBR was still existing on my hard drive.
Fixed it by using the "boot-repair" on a Live Ubuntu USB.

---

