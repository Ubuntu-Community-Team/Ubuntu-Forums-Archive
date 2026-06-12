---
title: "help: install problem with 6.10"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by hitboo on 2006-12-21
error happened:

irq 15: nobody cared (try booting with the "irqpoll" option).
....
Disabling IRQ #15.

-----------------------------------
My laptop is IBM R30. When I chose install option, this error will come out soon.

Thank you so much.

---

### Post by Sef on 2006-12-21
> Try booting **failsafe**

What devices do you have on irq 15?

If you can boot to a prompt try

dmesg | grep -i irq

This will show devices and their irq

From this DSL thread: [URL="http://www.damnsmalllinux.org/dsl-n/f/viewtopic/318.html"]IRQ Problems
[/URL]

---

### Post by hitboo on 2006-12-21
# dmesg | grep -i irq <enter>

...
ACPI: PCI interrupt link [pile] (IRQs 1 3 4 5 6 7 10 11 12 14 15)
...
ACPI: PCI interrupt 0000:00:10:.0[A]: no GSI - using IRQ 15
...
ide1 at 0x170-0x177, 0x376 on irq 15
...

Will these help?

---

### Post by Sef on 2006-12-22
> irq 15: nobody cared (try booting with the "irqpoll" option).

Did you try booting with the irqpoll option?

> ACPI: PCI interrupt link [pile] (IRQs 1 3 4 5 6 7 10 11 12 14 15)
...
ACPI: PCI interrupt 0000:00:10:.0[A]: no GSI - using IRQ 15
...
ide1 at 0x170-0x177, 0x376 on irq 15

It looks like it can't find the [GSI]("http://gsi.sourceforge.net/").  

Are you using the LIve CD?  If so, then download and burn the alternate cd.  It might work.  Otherwise I will have to investigate futher as to what to do.

---

### Post by hitboo on 2006-12-22
I'll try. Thanks.

---

