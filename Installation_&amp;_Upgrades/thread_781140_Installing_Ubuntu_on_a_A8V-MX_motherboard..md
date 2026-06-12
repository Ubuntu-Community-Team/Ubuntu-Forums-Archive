---
title: "Installing Ubuntu on a A8V-MX motherboard."
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by AAM on 2008-05-04
**Installing Ubuntu on a A8V-MX motherboard.**

The lack of recognistion of the SATA hard drive is a persistent problem (and I am writing this for my benefit as much as others).

Edit the GRUB command that loads the kernel to include at the end the following:

> irqpoll noapic pci=nomsiThen the SATA hard drive will be recognised. After installation you need to edit GRUB to include these parameters before re-booting AND whenever the kernel is upgraded (and GRUB re-written)

---

