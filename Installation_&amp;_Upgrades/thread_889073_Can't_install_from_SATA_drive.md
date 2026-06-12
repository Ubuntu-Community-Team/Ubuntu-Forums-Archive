---
title: "Can't install from SATA drive"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by Rakanishu on 2008-08-13
Got a SATA DVD, and when I boot the Linux installation I get something called "busybox".
When I use my IDE DVD, the same doesn't happen.

How do I install from the SATA drive? Since my HDD is IDE, and my motherboard only has one IDE cable, I have to open the case and put the DVD next to it everytime I install Ubuntu.

---

### Post by spiderbatdad on 2008-08-13
From the startup screen select F6. Delete the end of the kernel line "quiet splash --." add, "all_generic_ide"

---

### Post by Rakanishu on 2008-08-13
Works like a charm.
Thanks.

---

### Post by jcsaintpo on 2008-08-14
i just tried with Scsi Atapi drive
It doesn't work for me!
i/o errors searching ata drive

---

