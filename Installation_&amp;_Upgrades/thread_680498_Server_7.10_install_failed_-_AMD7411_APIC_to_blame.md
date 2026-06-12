---
title: "Server 7.10 install failed - AMD7411 APIC to blame?"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Starman97 on 2008-01-28
I've been trying to install the latest 7.10 Server Edition on a Tyan S2462 (AKA K7 Thunder).
I see this message: AMD7411: not 100% native mode: will probe irqs later 

and then later : lost interrupt

The CD boots ok and I've tried: noirqpoll  and noapic and also several variations of
setting the ide0=0x1f0,0x376,16 (17,18)
and also moving the cd to IDE1. 
It seems the IRQ never maps to the same thing I set in the kernel command line.

It seems to me that I need a kernel with native support for the AMD7411 built in.
This would get the correct IRQs for the IDE devices and allow me to complete the install
process without the 'lost interrupts' 

Is there an alternate kernel that I could drop into the .iso that has ADM7411 support?
Or do I have to build my own? I have an older Ubuntu 5 system running in the lab.

---

