---
title: "Error when installing"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by unclebensucks on 2008-07-31
I'm getting the following error when I try to install ubuntu on my very old machine:

ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
ACPI: Disabling ACPI support

What do I do now ?

---

### Post by linux_tech on 2008-07-31
What version of ubuntu? Make sure the version is correct, x86, 32bit. 

Update your bios, then  go into BIOS, locate Power Management section, and enable ACPI.

If this is not enough then try a different version of Ubuntu or at least a different cd.  When you load the cd,  hit F6, then add acpi=force

---

