---
title: "VIA C3 Segfaults in Install"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by jeremyh on 2008-04-04
During install on a VIA C3 (Samuel 2) 800Mhz it segfaults while installing the base system. I've tried installing 7.10 & 7.04 with no luck, I do know that Ubuntu is now optimized for 686 processors and the C3 is missing the cmov instruction. 

So has anyone had any luck installing it on a C3?

---

### Post by jeremyh on 2008-04-04
I have tried the alternate and the live cd installer, neither work. The live cd does boot up, but still fails during installation.

---

### Post by az on 2008-04-04
If this was a 686 kernel-problem, the installer on either the live or alternate cd would work fine, and the server kernel would not boot.  It would just continuously reboot.

It sounds like faulty hardware and not a software bug:
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by jeremyh on 2008-04-04
Yeah, I did think of that and switched out some RAM from my main machine, which didn't improve things. I didn't think of the hard drive as it's fairly new, but I'll try what it suggests.

Thanks for the reply.

---

