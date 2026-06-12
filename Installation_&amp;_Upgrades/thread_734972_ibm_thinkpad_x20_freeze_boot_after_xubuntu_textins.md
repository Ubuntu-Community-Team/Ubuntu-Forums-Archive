---
title: "ibm thinkpad x20 freeze boot after xubuntu textinstallation"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by KEEN23 on 2008-03-25
Hello

I just installed xubuntu-7.10-alternate-i386 on my ibm thinkpad x20 (2662) textinstallation.

now it will not boot.
It freezes after:

PCI: Found IRQ 11 for device 0000:00:0a.1
PCI: Sharing IRQ 11 with 0000:00:0a.0

I tried diffent approches in the grub-options:

root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=efa52d89-3c11-41b2....... ro acpi=off
initrd /boot/initrd.img-2.6.22-14-generic


also tried:  floppy=thinkpad, pci=noapci,  apci=off.

cansomeone  please help.

THX i.a.

KEEN

---

### Post by KEEN23 on 2008-07-14
Still have the problem now with 8.04.
It seems to be some sort of irq problem.
PLEAASEE HEEEELLP
I am researching  my *** off... still no solution.

last line befor getting stuck:
ACPI: PCI Interrupt 0000:00:0a.1[A] -> Link [LINKC] -> GSI 9 (level,low) -> IRQ 9

---

