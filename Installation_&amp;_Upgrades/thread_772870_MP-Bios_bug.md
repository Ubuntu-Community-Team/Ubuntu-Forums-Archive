---
title: "MP-Bios bug"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by Chaingeist on 2008-04-28
I'm trying to install Hardy Heron on my XP, and I was getting the busy box thing, so went to the forums and saw that somebody had said to type in "all_generic_ide floppy=off irqpoll" in at the boot menu under install. I did this and it came up saying "MP-BIOS Bug: 8254 timer not connected to IO-APIC" What does that mean and how do I fix it?

---

### Post by Xochipilli on 2008-09-04
I have the same problem. Did you find a solution?

---

### Post by Partyboi2 on 2008-09-04
you can try adding noapic as a boot option. If you are trying to install ubuntu at the main menu you can press F6 and add ```
noapic
``` at the end of the line.
Another thing you can try is to disable APIC in your bios
or try updating your bios.

---

### Post by The Question on 2008-10-18
I just wanted to reiterate the original poster's question.  I get the same error, "MP-BIOS Bug: 8254 timer not connected to IO-APIC" every time I boot up.  I did when I was running 7.04 too, running 7.10 now.  What does it mean and how do I fix it?  What's APIC?  What does turning it off do?  My manufacturer has no updates for my bios.

MAKE & MODEL: emachines T6212
CPU: 	AMD Athlon™ 64 3200+ Processor (with AMD 64 technology)
(2GHz, 2000MHz System Bus, 512KB L2 cache)
Operating System: 	Ubuntu 7.10 i386
Chipset: 	ATI Radeon® Xpress 200
Memory: 	512MB DDR (2 × 256MB), 400MHz Dual Channel
Video: 	ATI Radeon® Xpress 200 (PCI-Express® )
128MB shared video memory

---

