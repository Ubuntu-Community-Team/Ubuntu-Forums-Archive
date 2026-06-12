---
title: "Uncompressing Linux... ?"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by smith19 on 2007-07-29
Hey i am new to linux and i try to install ubuntu 6.02 live  it's says Uncompressing Linux...  ok ? booting the kernel. after that it will stop  i tried Disabling USB legacy from BiOS no luck. my box is 
intel core2duo e6600
ocz 2GB ram
WD 250GB HD SATA
SG 80GB SATA
LG DVDRW IDE

please help me i am kind of moving from windows. Thanks

---

### Post by Koybe on 2007-07-29
6.02 doesn't exist.

I suggest you pick the last version for your desktop, it could only be better. Feisty 7.04 is current. You'll find it on the main site. Grab it and burn it.


To pass trough your problem you could try booting without acpi. Boot on the cd and add these parameters to the boot : *noacpi acpi=off*

---

### Post by pcmanlin on 2007-07-29
i have the similar problem. after i refreshed the newest bios of motherboard, it is ok.

if not, you can try add kernel parameter to grub item, appending "debug" and deleting some about "splash", then paste the information here.

usually my work is to solve the similar problems.

first, plesae give some detailed information about your motherboard type.

:)

---

### Post by smith19 on 2007-07-29
i mean 6.06 not 6.02 sorry! 
my motherboard is GIGABYTE 965P-DS3 .

---

