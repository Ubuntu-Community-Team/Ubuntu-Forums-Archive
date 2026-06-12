---
title: "Gutsy: Setting up standard PCI resources"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by destinz on 2007-11-18
Hi 

While installing Gusty, I experienced the message :Setting up standard PCI resources" and the computer will just hang there.

Appreciate if anybody can help.

Thanks!

---

### Post by Millox on 2008-01-17
This also applies to one of my computers. No combination of noapic, nolapic, apic=ht works. Unfortunately the computer also does not have a working operating system so I can't check or post any lspci-output. The only thing I can say about it is that the motherboard is an AOpen-board, and the processor is a Pentium 4 @ 2 GHz. Mem is ok, according to memcheck86.

Does the alternate cd have the same kernel, or is it perhaps a good idea to try that one. Also, is it possible to use an alternate kernel using the already installed grub (kernel working, root fs borked).

Any ideas on how to proceed, my wife is getting really annoyed with me not fixing her computer ;-)

---

### Post by sig97 on 2008-02-04
Hi,

I had the same problem, even with the alternative CD. Eventually I got it started by specifying "acpi=off".

---

### Post by stooshbunutu on 2008-02-04
> **destinz said:**
> the computer will just hang there.
How long is this for because some processes do take a bout 30min without moving before the continue and the percent installation will not move either. Try using the alternate CD, I actually prefer this method. and make sure you check that the download is all there by using the MD5Sum checker applicationas described in the ubuntu official documentation and also run the "Check cd for defects" option on the installation menu.

I ended up going to sleep to let my installation run from that point.

Hope this helps :)

---

