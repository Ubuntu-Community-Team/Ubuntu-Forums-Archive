---
title: "dual core error"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2011-08-06
I used Knoppix on my system, it shows my Pentium 4 3200mhz as a dual core processor, on a asus/p4s800d mainboard and knoppix runs just fine.

I wish to use ubuntu 9.10x86-64 but when i try to install it, it reports that the processor is an i686 and is unable to boot.

which is right ubuntu or knoppix?

Thank you

---

### Post by oldos2er on 2011-08-06
I think early Pentium 4's were 32-bit, see [http://en.wikipedia.org/wiki/Pentium_4](http://en.wikipedia.org/wiki/Pentium_4)

cat /proc/cpuinfo should show more information.

---

