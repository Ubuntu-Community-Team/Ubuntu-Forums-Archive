---
title: "NEWBIE - Need help Booting from USB"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Jake P on 2010-01-26
Hi everyone,

I'd just like to know if there was someone who could give me link to a guide on how to boot Ubuntu from a USB. At the moment i am running Windows 7 64-Bit, i'll also need help on how to partition a HDD so that in the future i can Dual-Boot. As i said in the title i am completely new to Linux, and any help is greatly appreciated.

---

### Post by chewearn on 2010-01-26
> **Jake P said:**
> Hi everyone,

I'd just like to know if there was someone who could give me link to a guide on how to boot Ubuntu from a USB.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

>  At the moment i am running Windows 7 64-Bit, i'll also need help on how to partition a HDD so that in the future i can Dual-Boot. As i said in the title i am completely new to Linux, and any help is greatly appreciated.To re-partition Windows 7, use the built-in tool in Windows 7's Storage Management (find it somewhere deep in the Control Panel; I'm not running Windows 7, so I can't tell you exactly where it is).

Resize your existing partitions to free up some space (I suggest at least 10GB).  Keep the freed space as "empty and unallocated".  Then, when you run Ubuntu install, choose the option "Largest contiguous free space".

---

