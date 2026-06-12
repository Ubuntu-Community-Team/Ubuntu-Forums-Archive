---
title: "fail to install ubuntu10.10 on thinkpad E40"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by jazzi on 2010-12-28
> **My computer**: Thinkpad E40(edge 14' with intel)
(CPU: P6100,Chipset:Intel HM55,Video:integrated)
**Ubuntu**:10.10

This laptop is absolutely new, I use ubuntu 10.10 DVD to install and seems everything is perfect, after finish installation and reboot, it can't boot successfully even can't get the welcome screen.

But when I hit the power button to shut down, the ugly screen shows out and tell me it's trying to terminate the system.

Can ubuntu10.10 be installed on E40?

thanks
jazzi

---

### Post by jazzi on 2010-12-29
Finally I think I find the answer after visiting the thinkpad service center.

The point of this problem is in the BIOS, we should change the SATA mode from AHCI to Compitable.

> BIOS--> Config-->Select Serial ATA (SATA),change 'AHCI' to 'Compatibility'

---

### Post by jazzi on 2010-12-29
I thought it shoule work because windowsXP work but I tried the whole night and result the same problem.

I'll try the lower edition like ubuttu10.04 and see.

Don't know why, so curious.

---

### Post by jazzi on 2010-12-30
Yesterday  night I made some trying,first, I burn another ubuntu10.10 CD and results the same problem.

then I tried Ubuntu10.04 and God it worked, everything works just great.

So have to use 10.04 and wait for another long-term support edition.

---

