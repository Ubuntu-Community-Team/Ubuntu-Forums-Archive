---
title: "Installer Hangs Early On (APIC?)"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by ObsidianOps on 2006-06-28
Hello!

When i select install on the desktop cd, it gets past the first menu, to where it's loading the "Restricted Drivers", and then it dies quickly.

It seems to die slightly differently each time (A kernel panic, a preempt thinger, some other thinger...)

I see a lot of mentions of a SMP_APIC_INTERUPT_TIMER or something.

It's a HP computer with an Intel motherboard/chipset, SATA hard drive, and an ATI board.

Any idea where to look to fix this? o.O
Thanks!

---

### Post by doonium on 2006-06-28
you can try appending  'noapic' to your kernel paramters list

to do this, when the installer menu comes up, hit f6
then type 'noapic' and hit enter

---

