---
title: "Upgrading from an AMD to an intel system"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by jaalburquerque on 2016-08-05
Hi.  I've been running an amd64 system for many years now (about 10) and am happy with how it's been functioning.  My system is presently running ubuntu 16.04.  I'm thinking of upgrading to a new computer system but keeping my hard drive with the presently installed OS (and apps, etc) in place.  I'm wondering if it is just possible to take the drive out of the present system and place it in a new system if the new system has an intel CPU instead of an AMD one.  Thanks for any clarifications.

---

### Post by howefield on 2016-08-05
Chances are high that you'll be ok especially if the new hardware is well supported in Linux. Might be best to disable any proprietary graphics drivers if you are moving from one graphics card vendor to another.

---

### Post by grahammechanical on 2016-08-05
The big issue is not the CPU but the GPU (video adapter).

64 bit Ubuntu (amd64 ISO image) will run on both Intel and AMD 64 bit CPUs. Whereas, 32 bit Ubuntu (i386 ISO image) will run on both Intel and AMD 32 bit CPUs and because of the backward compatibility of the 64 bit architecture 32 bit Ubuntu (i386 ISO image) will also run on 64 bit AMD & Intel CPUs.

Before you swap the hard drive out you should revert to using the open source video driver. Even if the video adapter in the new machine is made by the same manufacturer as the video adapter in the old machine, the newer video adapter may need a different video driver. The proprietary video driver in the old machine may not support the newer video adapter.

Regards.

---

### Post by jaalburquerque on 2016-08-09
Thank you for your answers; they are very helpful.

---

