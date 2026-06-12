---
title: "any alternative to busybox?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by CRXLNX on 2008-01-06
I have my system booting into rescue mode but it still puts me into busybox.
I thought I would get a real shell.

is there a way to get the cd (alt-cd) to use a different shell?

I need bzip and other things this toy shell does not have

---

### Post by Pumalite on 2008-01-06
Busy box means you have incompatible hardware.

---

### Post by Pumalite on 2008-01-06
You could try your luck with some boot parameters:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

