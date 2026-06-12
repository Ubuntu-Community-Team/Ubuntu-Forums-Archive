---
title: "Upgrade from 32 to 64 bit Ubuntu"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by Verzicht on 2005-10-17
Can anybody tell me, how to upgrade my Ubuntu 5.06 i375 to Ubuntu 5.06 AMD64 without destroying information?

---

### Post by sjwaste on 2007-07-01
Bumping this thread.  Does anyone know if you can upgrade 32 bit to 64 bit on an existing install?

Thanks!

---

### Post by mikewhatever on 2007-07-01
Download an iso of the 64 bits version and burn to a CD. Backup important data, and reinstall. Upgrading..., don't think so.

---

### Post by PgR on 2007-08-24
Does anyone know if this is still the case in 7.04? Will it be in 7.10?

---

### Post by upbeat.linux on 2007-09-25
Currently running 7.04 (32-bit on a 64-bit processor) and I experienced the double timing issue until I added:

```
noapic acpi=off
```

Not sure if its been resolved in 7.10. 24 more days until we find out.....

---

