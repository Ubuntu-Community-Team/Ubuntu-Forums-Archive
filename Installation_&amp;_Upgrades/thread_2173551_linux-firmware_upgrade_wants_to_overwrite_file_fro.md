---
title: "linux-firmware upgrade wants to overwrite file from 3.0 linux-firmware-image on 12.04"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by User4519 on 2013-09-10
Hi :)

I'm running Ubuntu Server 12.04.3 on a machine here.

Due to compatibility issues with more recent kernels and my SATA port multipliers, I'm running kernel version 3.0.69, and therefore I also run [FONT=courier new]linux-firmware-image[/FONT] version 3.0.69-1.

My problem is that the last two updates to the [FONT=courier new]linux-firmware[/FONT] package (1.79.5 and 1.79.6) both want to overwrite [FONT=courier new]/lib/firmware/intelliport2.bin[/FONT] which is provided by my (older) [FONT=courier new]linux-firmware-image[/FONT] package, and so apt-get errors out with:

```
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.79.6_all.deb (--unpack):
 trying to overwrite '/lib/firmware/intelliport2.bin', which is also in package linux-firmware-image 3.0.69-1
```

This is understandable &#8212; I'm guessing there's been a change recently with regards to which package supplies this file. I'm just not sure how to deal with it, seeing as how I'm still on an older kernel. I'm wondering if I should keep back updates to the [FONT=courier new]linux-firmware[/FONT] package altogether, or if I should resolve this issue in another way. Seeing as there's no one-to-one relationship between the version numbers on [FONT=courier new]linux-firmware[/FONT] and the kernel packages, this wasn't immediately logical to me, and so I've chosen just to keep back all "kernel-ish" package updates by locking down those packages that match my kernel version, that is [FONT=courier new]linux-firmware-image[/FONT], [FONT=courier new]linux-headers[/FONT], and [FONT=courier new]linux-image[/FONT] (all 3.0.69-1).

What do you think? Lock down linux-firmware to its current version or resolve otherwise?

Thanks in advance,
Daniel

---

