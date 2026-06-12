---
title: "installation question"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by aciby on 2007-01-16
hi

very new to linux, basically trying to get an install done and then to learn....


im stuck on the install though.. seems to me to be a problem... yet things seem to work

after a fresh install... after start up i get the following messages

setup_irq: irq hadler mismatch
acpi: sci (irq0) allocatin failed
acpi: unable to start the acpi interpeter
shpchp: shpc_init: canot reserve MMIO region


i understand there is prob assigning irq0, not sure what it is using zero for .... but no idea if the following lines are related or something different



appreciate any help

cheers

---

### Post by aciby on 2007-01-17
normally i would just delete the link from my favourites...... but thought this time ill at least say....thanks :).....and then delete

---

### Post by 23meg on 2007-01-17
Try booting with the "acpi=noirq" kernel parameter. In the GRUB boot menu, choose your kernel line and hit "e" to edit it, find the line that goes like ```
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash

```and put "acpi=noirq" at the end of it.

---

