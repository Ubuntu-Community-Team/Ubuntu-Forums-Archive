---
title: "Problem with IRQ"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by Demuri on 2006-03-12
Hi,
I'm trying to set up Kubuntu 5.10 on my PC. AMD Athlon 64, 2000 MHz (10 x 200) 3000+, motherboard Asus K8N4-E Deluxe (3 PCI, 3 PCI-E x1, 1 PCI-E x16, 3 DDR DIMM, Audio, Gigabit LAN, IEEE-1394), chipset nVIDIA nForce4-4X, AMD Hammer, BIOS Award (09/08/05). But installation freezed at string "Disabling IRQ #11". boot option "linux pci=noacpi" doesn't help... So what can I do with it?

---

### Post by 5-HT on 2006-03-12
Not sure if it'll help, but what about trying either 'irqpoll', or maybe disabling acpi (can be a cause to some irq issues) with 'acpi=off noacpi'?

---

### Post by Demuri on 2006-03-12
I tried option "linux pci=noacpi" (ubuntu's boot help). I thoght problem is about ACPI, but result is the same. How to disable this ummm... IRQ disabling?

---

### Post by 5-HT on 2006-03-12
Did any of the two options I mentioned work at all?

---

### Post by Demuri on 2006-03-12
Yes! Yes! :) irqpoll works :) Congratulations to me - I'm blind idiot. Few strings before "Disabling IRQ #11" - "Try to use option irqpoll". So boot: linux irqpoll helps. Thanks in advice pal.

---

### Post by Felix21685 on 2006-03-12
hey guys..

im having a similar issue 
except my issues are that it loads all hte drivers and stops 
on
etc/hotplug/ide.rc  which is right after PCI and USB.

ive tried acpi=off noacpi..

no dice.
anyone know what i should try?

---

