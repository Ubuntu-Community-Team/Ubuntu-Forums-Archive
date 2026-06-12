---
title: "Fiesty Fawn: Linux Kernal - generic Vs 386"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by eabhi on 2007-06-22
Whats the difference between the Linux Kernel Image -generic and -386??? which one is the best for AMD Athlon XP Processors???

I have Desktop and laptop both having 32-bit AMD Athlon XP Processors. I have Clean installed Feisty Fawn on the Desktop and upgraded from Ubuntu 6.06->6.10->7.04 on the laptop.

Now the case is that the Desktop uses the "-generic" Kernel image while the Laptop uses the "-386" kernel. If both have the same Processor, why is the installations using the different type/flavour of the Kernel :(

Please let me know which oe is the best of both and how to switch to the one from the other kernel. :)

Cheers
eabhi

---

### Post by ermannobonifazi on 2007-07-08
The -386 kernel doesn't have SMP enabled, and doesn't use the GCC -generic optimisation target. It's basically there to support some old, buggy drivers that don't work with SMP enabled.
Generic offers also better support for Hypertreading CPU

---

