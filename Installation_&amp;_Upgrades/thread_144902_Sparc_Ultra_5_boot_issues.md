---
title: "Sparc Ultra 5 boot issues"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by garthoid on 2006-03-15
Hi,

I have downloaded and installed Dapper Drake for sparc on my Sparc Ultra 5.
The install completed without issue.

But when I boot the system I get a boot prompt after the phrase "FP Disabled".

Any clues?

What release would you recommend?

Thanks in advance,
G

---

### Post by garthoid on 2006-03-16
Powered down the system and power up and the system boots. I can see the ubuntu screen. Strange.

---

### Post by SchlingBlade on 2006-05-29
That worked for me as well on my Ultra2 system.  Set the boot-device to the CD-ROM in prom (probably not needed, but what the heck), booted fine.  Then it failed to detect my CD-ROM (SCSI system), so I went to another terminal window and did "modprobe esp", redetected the CD-ROM, and so far so good.

Definately strange.

---

