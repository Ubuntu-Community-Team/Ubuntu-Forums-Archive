---
title: "Ubuntu on Asus 1215T"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by jbraum on 2010-12-25
Just go a new laptop Asus 12.1 1215T and am trying to install 10.10 but I am hanging at ohci_hcd 0000:00 12.1: irq 16, io mem 0xfbbfd000 towards the beginning of the install.  Has anyone had this problem, if so what are possible solutions.

---

### Post by dino99 on 2010-12-25
on the boot line (F6) add & play with either: noacpi, nomodeset, nolapic, noapic, irqpoll

but firstly, check the bios settings, mainly about irq (not assigned) and "extended usb" if its exist

---

### Post by jbraum on 2010-12-25
Sorry for the stupid question but when would I f6?  Thanks for the help.

---

