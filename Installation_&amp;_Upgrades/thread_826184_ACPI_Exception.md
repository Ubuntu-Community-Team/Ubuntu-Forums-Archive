---
title: "ACPI Exception"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by ayharano on 2008-06-11
Hello there.

I had installed Ubuntu 7.10 64 bits edition on an Acer 5050-3284. I had some problems using it, like having a black screen during start up, however I could login after a while.

Today I tried to install Ubuntu 8.04 32 bits edition at the same computer as a fresh new installation. I tried to install but the progress bar wouldn't move. I tried to check the CD and it wasn't even beginning the test.

I tried to install through wubi. I used the verbose mode of installation and finally got the problem.

> ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]

I would really appreciate if someone help me out.

Thanks in advance.

---

### Post by Pumalite on 2008-06-11
Edit your boot line and add one of these parameters (alone or in combination):
noapic nolapic acpi=off pci=noacpi

---

