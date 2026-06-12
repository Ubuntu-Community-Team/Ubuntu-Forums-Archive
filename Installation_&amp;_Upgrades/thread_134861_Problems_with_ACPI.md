---
title: "Problems with ACPI"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by Monomachus on 2006-02-22
from live CD I receive smth like that :

[4294668.038000] ACPI: Looking for DSDT in initrd...not found
[4294668.084000] not found!
[4294668.094000] ACPI: setting ELCR to 0200 (from 0e20)

when I try boot: live acpi=off I receive almost the same thing.

[80.594881] Cheking for popad bug...OK
[80.595110] checking if image is initramfs...it isn't (no cpio magic); looks like an                                 initrd   
[80.809923] Freeing initrd memory: 3963k freed.

What's wrong & what should I do to fix the problem?

---

### Post by Monomachus on 2006-02-26
the problem was solved  I needed to write
```
linux vga=771 noapic nolapic 
```

---

