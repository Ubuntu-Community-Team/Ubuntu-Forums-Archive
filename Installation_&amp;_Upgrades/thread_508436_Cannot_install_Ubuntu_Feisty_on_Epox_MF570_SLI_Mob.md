---
title: "Cannot install Ubuntu Feisty on Epox MF570 SLI Mobo"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by frdr09 on 2007-07-24
AMD Athlon 64 X2 3800 Brisbane
Epox MF570 SLI
2x512 MB RAM DDR2 533
80 GB SATA Seagate Barracuda

I cannot install ubuntu feisty fawn these words came out from the screen

[37.623837].. MP-BIOS Bug: 8254 Timer not connected to I/O-APIC
[37.802644] Kernel Panic-not Syncing: to APIC + Timer Does'nt work 
Boot with APIC = debug and send a report. Then try booting with the noapic option
[37.802693]


Could someone help me please. I really want to install Ubuntu Feisty

---

### Post by loki0347 on 2008-04-10
I have this mobo as well. I'm going to assume that you are using the live CD. When it first starts up you need to hit the F key that says more options, F7 I think. It will show you a long command that starts the Linux kernel at the end of it type 'noapic' without the quotes, and you should be in business. Best of Luck to your Linux conversion.

---

