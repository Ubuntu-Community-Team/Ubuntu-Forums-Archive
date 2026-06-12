---
title: "Wubi on Windows Vista"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by jechadwell99 on 2013-08-21
Does Wubi work on Windows Vista? Is it risk-free to install? Also, if the version of Vista that you have is slow and glitchy does that mean Ubuntu will run slow and glitchy?

---

### Post by prodigy_ on 2013-08-21
Wubi is discontinued but it's still available in 12.04 and should be compatible with Vista. Wubi was supposed to provide an easy way to try Ubuntu on a Windows PC without the need for a virtualized environment. Arguably it fell short of expectations for various reasons (mostly due to technical limitations of such approaches). As far as I can tell, Wubi was just as likely to cause issues as a native dual-boot setup.

I'd suggest using a virtual machine (e.g. VMWare or VirtualBox) if you just want to try Linux or a regular installation (without Wubi) if you're going to use Linux extensively.

---

### Post by Mark Phelps on 2013-08-21
I found Vista to be "slow and glitchy" when I first used it (instead of XP) -- but I addressed that by doubling the system memory from 1GB to 2GB.  After that, it ran nearly as quickly as did XP earlier.  So, if you only have 1GB of system memory, Vista is not going to be very fast.

As to the "speed" of Ubuntu, older releases tend to be snappier than newer ones.  Version 12.04 should provide a snappier system than Vista -- but some of that run time performance is going to depend on the video drivers -- and those are different in Linux than they are in MS Windows.

Also, hardware drivers are likely to be an issue -- since Linux drivers are generally not provided by the OEMs from which you buy MS Windows PCs.

I would first boot from a LiveCD/LiveDVD,LiveUSB of Ubuntu and see how well it detects your hardware and installs the drivers.  Anything that does not work needs to be researched to see if drivers can be found for it; otherwise, you would have to live without it working.

Unless you have a LOT of memory (4GB, for example), I would not run Linux in a VM.  Vista is slow enough as is, and if you only have 1GB of memory, you're going to be giving probably ony 512MB of memory to Ubuntu, and it's not going to perform well with that.

---

