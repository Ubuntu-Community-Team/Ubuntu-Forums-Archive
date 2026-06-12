---
title: "VIA VT6421 won't boot 10.10 x64"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by imrazor on 2011-02-22
I've run across a weird problem. My IDE DVD drive is connected to a a generic VIA VT6421 PCI card with an IDE port (SATA ports are unused/disabled). The Ubuntu 10.10 x64 DVD will not boot. My computer will not recognize it. I tested the CD in another 64-bit PC, and it booted fine. To compound the weirdness, I've found that an Ubuntu 10.10 i386 (aka 32-bit) CD will boot just fine. Huh? Anyone have any idea what's going on?

---

### Post by mörgæs on 2011-02-23
I don't have an exact explanation, but it is not uncommon that only the 32 bit versions works, though the computer is 64 bit - are you absolutely sure about the latter, by the way?

---

### Post by imrazor on 2011-02-26
> **mörgæs said:**
> I don't have an exact explanation, but it is not uncommon that only the 32 bit versions works, though the computer is 64 bit - are you absolutely sure about the latter, by the way?

I "solved" this issue by connecting my DVD-R to my motherboard's onboard IDE controller. Once it was hooked to the onboard controller, the x64 CD was recognized, and I was able to boot and install 10.10. So it appears that Ubuntu x64 LiveCD doesn't support the VIA VT6421 (or at least booting from it.) Can anyone confirm this? A bit strange, considering Linux's reputation for supporting legacy hardware.

---

