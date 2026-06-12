---
title: "Ubunut 9.10 and AHCI"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by Eisenhorn on 2009-12-20
I am trying to intall ubuntu 9.10 on a SATA drive with AHCI enabled. The installation program doesn't recognize any disk. When i boot the live system i can start GParted which will find /dev/sda. I can format the partion and mount it. Still when starting the installtion program out of the live system i will not find any disk/partion.

```

lsmod | grep sata
lsmod | grep ahci

```

doesn't show anything. But the drivers must be loaded as i can manipuilate the disk with GParted.

I am using x86 version.

System:

Asus P5Q PRO
E8400
9800GTX+

Is there another way to install the system?

---

### Post by Eisenhorn on 2009-12-22
Has really nobody an idea?

---

