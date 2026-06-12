---
title: "XUbuntu 8.04 in my old computer"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by rootribal on 2008-09-16
Hello,

I want to install in my old computer XUbuntu 8.04:
+ CPU Type: PENTIUM II-MMX
+ CPU Clock: 350 MHz
+ Extended Memory: 326656K

I have the next error:
[0.00000] ACPI: BIOS age(1998) fails cutoff(2000),
          acpi=force is required

---

### Post by darrelljon on 2008-09-16
Type acpi=force as a boot parameter.

---

### Post by rootribal on 2008-09-16
Hello again,

I typed acpi=force but I had this error:
ACPI: Unable to load the System Description Table

---

### Post by rpm13 on 2008-09-16
Try acpi=off

---

### Post by oilchangeguy on 2008-09-16
> **rootribal said:**
> Hello,

I want to install in my old computer XUbuntu 8.04:
+ CPU Type: PENTIUM II-MMX
+ CPU Clock: 350 MHz
+ Extended Memory: 326656K

I have the next error:
[0.00000] ACPI: BIOS age(1998) fails cutoff(2000),
          acpi=force is required

you may want to consider puppy linux, or damn small linux for your antique. if you're wanting to learn about ubuntu or linux in general an antique computer is not a good place to start. many distros are available as live cd's and you can take 'em for a test drive on a newer more powerful computer. without making any changes to the computer.

---

### Post by user11 on 2009-01-11
Right, Xubuntu should do fine on there. I'm using Xubuntu 8.10 on a Pentium II 300 MHz Presario 5030 with 256 pc100 ram while I'm typing this.

Does the install continue past the ACPI notification? I generally just ignore it when I boot up my fully functional "antique".

---

