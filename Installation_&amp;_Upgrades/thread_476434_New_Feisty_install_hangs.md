---
title: "New Feisty install hangs"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by IcarusR on 2007-06-17
I have managed to install Feisty, but when I try to boot it hangs with 'Starting up' on the screen.
If I boot in 'recovery mode' it gets as far as...

[  27.838153] CPU0: AMD Semperon(tm)  2200+  stepping  01

I have had Dapper running on this system.

Can any one give me any ideas how to resolve this ??

---

### Post by IcarusR on 2007-06-17
Just noticed that the previous line reads...

[ 42.425099] ACPI: Core revision 20060707 not found!

If I use boot option  noacpi then it reads....

[ 42.425099] ACPI: Core revision 20060707 not found!
[ 27.838153] CPU0: AMD Semperon(tm) 2200+ stepping 01

If I use boot option  noacpi & nolapic then it reads....

[ 42.425099] ACPI: Core revision 20060707 not found!
[ 42.430905] ACPI: setting ELCR to 0200 (from 0ea0)
[ 27.838153] CPU0: AMD Semperon(tm) 2200+ stepping 01

What ever I use it still hangs at the same place.

---

### Post by IcarusR on 2007-06-17
Tried booting with acpi=off but makes no difference, still hangs at...

[ 27.838153] CPU0: AMD Semperon(tm) 2200+ stepping 01

I'm guessing that something doesn't like that CPU !!????

---

### Post by Pumalite on 2007-06-17
> **IcarusR said:**
> Tried booting with acpi=off but makes no difference, still hangs at...

[ 27.838153] CPU0: AMD Semperon(tm) 2200+ stepping 01

I'm guessing that something doesn't like that CPU !!????

What are you installing: Feisty 32bits or Feisty64bits?

---

### Post by IcarusR on 2007-06-17
I believe it was 32 bit

---

### Post by Pumalite on 2007-06-17
> **IcarusR said:**
> I believe it was 32 bit

Check for hardware incompatibilities. 32bit should work fine in 64bit and you have a better  and larger choice of packages. Check your BIOS. Update it if possible. Check your hard drives. A mix of SATA and IDE is no good. What chipset do you have? Check in Searck for possible problems with your hardware. I f all is OK, then consider that all OSe's like to reside alone in a hard drive. Installation is easier if you choose 'Guided>Use Entire Disk'. Also is better to use Gparted to prepare your disk and create new partitions ( format to ext3 ). Then install again if you need to.

---

