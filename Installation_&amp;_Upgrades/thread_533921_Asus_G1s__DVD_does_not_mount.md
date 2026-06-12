---
title: "Asus G1s:  DVD does not mount"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by jdjacobs on 2007-08-24
I have a new Asus G1s. When a DVD is inserted, it apparently is not mounted. No file such as /dev/hda1, /dev/dvd, or /dev/cdrom is created in /dev. /etc/fstab has the line:

```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I have seen a number of other Asus G1s that appear to have the same problem. But I have not seen the fix.

Thanks,

---

### Post by Pumalite on 2007-08-24
Go to BIOS>IDE Configuration>Enhanced Support for PATA+SATA

---

