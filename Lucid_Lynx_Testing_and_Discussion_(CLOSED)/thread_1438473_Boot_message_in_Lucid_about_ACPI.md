---
title: "Boot message in Lucid about ACPI"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MartinuxP on 2010-03-25
When I boot my ubuntu lucid I get this message:
```
[    6.299886] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SMRG [0xb00-0xb0f]
[    6.299932] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```
Then the machine starts normally.
Is this a problem?

bye.

---

### Post by afrodeity on 2010-04-13
There doesn't seem to be a way to turn acpi off with the new installer. I tested Lucid Beta 1 on my Dell, and no go.

---

### Post by lucazade on 2010-04-13
You could try to blacklist the piix4 module

sudo gedit /etc/modprobe.d/blacklist.conf

blacklist i2c_piix4

---

