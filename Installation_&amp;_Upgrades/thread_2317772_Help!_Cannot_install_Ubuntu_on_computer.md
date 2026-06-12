---
title: "Help! Cannot install Ubuntu on computer"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by jibuti on 2016-03-19
I tried to install Ubuntu on my new computer but was unable to do so. I first tried to install alongside Windows 10. Errors I received include "ubi-partman failed with exit code 141", "ubi-timezone failed with exit code 1", etc. I first thought it was uefi or windows bootloader's problem. But same error happened for me when I swapped for a new hard drive with nothing on it. 
The "try Ubuntu without installation" option doesn't work either. It would boot into system and then freeze. I get the error message "0 disk space available". I am unable to start gparted or any other program.
I am using 14.04. I am fairly sure the installation media is fine as I used it to install on older computers with no problem. 
It seems Ubuntu is unable to control my hard drive or memory correctly.
I am running 16GB DDR4 memory on a H110 motherboard with i7 6700.

---

### Post by jibuti on 2016-03-19
To summarize the symptoms during installation. Ubuntu cannot write to my hard drive or store any information. Memory overflows and causes system to fail.

---

### Post by buzzingrobot on 2016-03-19
It *may *be the Skylake processor.  I don't think there's any Skylake support in the 3.13 kernel that ships with 14.04. Try something with a 4-series kernel, the later, the better. 14.04.04 ships with 4.2, and 16.04 is using a 4.4 kernel.

I'm using 16.04 on an i5 Intel Skylake 6260 and it's unstable with anything other than a 4.5 kernel.

This page at the Arch wiki discusses some of the problems and offers some workarounds. I'm using  the "i915.enable_rc6=0" kernel parameter it suggests.

---

