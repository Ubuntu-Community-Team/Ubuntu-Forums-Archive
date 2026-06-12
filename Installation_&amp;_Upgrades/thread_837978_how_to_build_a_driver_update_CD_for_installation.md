---
title: "how to build a driver update CD for installation?"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by ahkunchan on 2008-06-23
Hi all,

I have a chance to get a new H/W for testing. But I found there is an installation problem of Ubuntu 8.04.
It's because the storage driver of the H/W isn't included in the kernel of Ubuntu 8.04.

I'm trying to build the driver update CD for me to install the OS successfully. But I could not find the document which teaches users to build the "driver update CD".

Meanwhile, I just knew to build the deb package and placed it to 
"ubuntu-drivers/2.6.24-16-generic/xxx.deb".
But it still failed to work.

Any idea on this? Or give me a hint to do next. :confused:
T.I.A.

In addition, I've built the updated driver and it worked in the platform.

BRs,
ahkunchan

---

### Post by ahkunchan on 2008-06-24
:( 
I guess I've done the driver update CD.

Now, I faced a problem. That is,
the stroge default driver (pata_xxx) has been loaded by initrd.gz of Ubuntu 8.04.
But I want to use the new one (pata_xxx) which I built.

Is there any way to disable the origianl pata_xxx driver, and load the my driver successfully?

In addition, I have a workaround for this case. But it seems not good enough.
That's is to install the OS with my driver update CD via an external USB DVD/CD ROM. Then doing some tricky steps.

Fianl, I know to remaster the install CD is also a way to fix my problem. But I still want to make the driver update CD workable without remastering the CD.

Any ideas? Thanks.

AhkunChan

---

### Post by ahkunchan on 2008-06-24
As I know, the Fedora/SuSE have ways to load the driver disk which lets users to load the new driver prior to original ones.

Why not Ubuntu? Or I didn't find out the way? Thanks.

---

