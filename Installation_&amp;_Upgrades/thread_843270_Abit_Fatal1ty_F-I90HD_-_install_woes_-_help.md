---
title: "Abit Fatal1ty F-I90HD - install woes - help"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by rob martin on 2008-06-28
Hi 

Have just purchased one of these boards - I've an all sata config i.e. sata dvdrom and hard discs.  The issue is that I can't install 8.04.  The installer hangs after loading the kernel just a flashing cursor at the top of the screen.  I know this is an issue with the sata dvdrw and the installer so I've tired the following options (to no avail) all_generic_ide irqpoll noapic nolapic 

I've also tried numerous BIOS Sata options from AHCI to Legacy IDE again no luck.  Could someone/anyone who has successfully install Ubuntu with a similar config please help?

---

### Post by rob martin on 2008-06-28
Ok At least I now know its not a problem with the hardware.  Fedora 9 installing as I write.  

I be grateful if anyone could suggest a work around before the installer finishes, feel like a soviet era defector.:(

---

### Post by rob martin on 2008-06-28
For those who have the same problems as described above press F6 at the install screen and add
clocksource=acpi_pm to the kernel options.

---

