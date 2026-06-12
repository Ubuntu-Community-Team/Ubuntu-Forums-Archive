---
title: "USB stick dead?"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-10-14
I tried to create a startup USB stick using the GNOME USB startup disk creator. I was not aware that it failed, but I could not boot from tyhe stick. Now I cannot do anything with the stick. gparted, palimpsest and the startup disk creator all fail to create a partition table, dmesg says sdg: unknown partition table, and in windows, format fails and swissknife tells me the stick is read-only (it has no switch on it to make it read-only)

Is it dead? Is there any lower level tool I can use to thrash it?

TIA

---

### Post by girto on 2009-10-14
Try the HP USB Disk Storage Format Tool (freeware but Windows only)

It fixes a lot of things other packages can't fix.

---

### Post by Merk42 on 2009-10-14
> **girto said:**
> Try the HP USB Disk Storage Format Tool (freeware but Windows only)

It fixes a lot of things other packages can't fix.

Darn, tried it on mine, it shows 0MB, so I guess it's just dead.:(

---

