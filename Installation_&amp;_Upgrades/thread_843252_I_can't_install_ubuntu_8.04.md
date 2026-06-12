---
title: "I can't install ubuntu 8.04"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by chanfle on 2008-06-28
Currently I use 7.10, and I could not install 8.04 when booted la computer with CD into appear me the next message "BIOS BUG FOUND", disable apci and apic in the start menu ubuntu with F6.
I install it but the cooler CPU becomes very hot and shutdown the computer.
How I can use the Ubuntu 8.04...???
Spec's my laptop:
Acer 5050
ATI Xpress 1100,
AMD Turion 2.2 GHz,
1 RAM,
80 HDD
ODD DVD/CD 
Wirelles Atheros

I waiting your response.....

---

### Post by Pumalite on 2008-06-28
Edit your boot line:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
And try:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off 
One at the time or in different combinations until you hit the right one.

---

### Post by AlexBellisBrown on 2008-06-28
Also, have you tried updating via the update manager? Its probably better than using the Live CD.

---

### Post by oldos2er on 2008-06-28
You might want to look into updating your BIOS.

---

### Post by chanfle on 2008-06-29
hi all
thanks for replay your comments....
on this moment i install clean 8.04, in other post in this forum i found how i can fix my problem....with DSDT application....
let me finish my installation and i comments later...

regards....

---

### Post by chanfle on 2008-06-29
hi all
I'm working my Hardy, but some time my CPU cooler is hot.....i installed DSDT...
any comments...???

---

