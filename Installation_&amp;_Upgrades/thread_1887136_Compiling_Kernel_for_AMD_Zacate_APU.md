---
title: "Compiling Kernel for AMD Zacate APU"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by carlexpc on 2011-11-26
Hi All,

I bought an ASRock E350M1 motherboard which has AMD Zacate E350 APU. I am in the process of compiling a kernel for it but I can't decide which among the processor types should I select that would make the kernel work with Zacate, at least safely. To date, there is no specific item in the list that is solely for Zacate just like what Intel Atom have.

Which among the processor list in the kernel config is the most optimal choice? Any recommendation is greatly appreciated.

TIA,

Carlex

---

### Post by dino99 on 2011-11-26
I always use compiled kernel (as im too lazy :)) from ubuntu archive. Since 2.6.38, zacate works without tweaking

[http://www.kadisera.com/2011/linux-2-6-38-compatible-with-apu-and-zacate-ontario.html](http://www.kadisera.com/2011/linux-2-6-38-compatible-with-apu-and-zacate-ontario.html)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
- select one and download it into an empty folder
- install needs 3 packages: headers.all, header, image (select either i386 for 32 bits (i386-pae if ram >3 gb) or amd64 for 64 bits installation
- then cd to that folder and: sudo dpkg -i * (needs built-essential & dkms previously installed)

---

