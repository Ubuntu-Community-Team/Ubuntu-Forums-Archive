---
title: "CD fails to mount in Karmic after applying latest updates"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nIRV on 2009-09-17
Since September 16/17, Ubuntu Karmic fails to mount CDs/DVDs. Anyone else suffering from same issue?

---

### Post by VMC on 2009-09-17
I just noticed this last night. 

The weird thing is after I used the feature to open Brasero to burn a disk, then inserted a cd it recognized it and burnt it.

Use this in meantime to mount and unmount:

```
sudo mount -t iso9660 -o ro /dev/cdrom /cdrom
sudo umount /cdrom
```

---

### Post by nIRV on 2009-09-17
> **VMC said:**
> I just noticed this last night. 

The weird thing is after I used the feature to open Brasero to burn a disk, then inserted a cd it recognized it and burnt it.

Use this in meantime to mount and unmount:

```
sudo mount -t iso9660 -o ro /dev/cdrom /cdrom
sudo umount /cdrom
```

Thanks for the workaround. Any idea whether a launchpad bug was filed?

---

### Post by Robin Nixon on 2009-09-17
> **nIRV said:**
> Thanks for the workaround. Any idea whether a launchpad bug was filed?

Apparently several...

---

