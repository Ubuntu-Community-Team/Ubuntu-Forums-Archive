---
title: "ubuntu 6.0.6.1 server, system won't start after installation"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by DirkH on 2006-10-31
Hi,

If have installed ubuntu 6.0.6.1 lamp server on a old pc (AMK-K6 / 200) with 256 Mbyte memory.

The installations seems successfull but when i start the system it reboot everytime after the boot command from grub.

I tryed installing with LILO boot loader and then i see that the kernel is loaded and get a message about the bios (reading bios parrameter or something like that) en then the system restarts.

I installed a old SUSE version (8.0) without anny problems, this works but with ubuntu i tryed different versions (dapper, 6.0.6, 6.0.6.1 6.10) and none of these seems to start.

Can somebody help me with debugging this problem.

I already tryed apic=off  etc... and nothing seems to help

Dirk (Belgium)

---

### Post by Iowan on 2006-11-07
Can you boot into the recovery mode - or from the LiveCD?

---

### Post by mike_d on 2006-11-09
any solution to this problem?  i'm experiencing the same thing after installing both dapper server and edgy server on a pentium-166.

---

### Post by CyberX on 2006-11-10
Hi.
I had the very same problem but I found somewhere here that the server kernell was compiled for 686 and higher only (I was also using a K6).
I read that it is possible to change the kernel just before the server installation ends, but then I already reinstalled with the Alternate CD.

---

