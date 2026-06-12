---
title: "Alternate install destroyed sdb1 partition"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shram on 2009-10-27
The alternate install method wrote to the partition table of my second hardrive after asking it to use /dev/sdb1  for /var/cache/apt/archives.
I don't think this drive's partition table should have been written to with no boot element being used on data drive.

---

### Post by fancypiper on 2009-10-27
You shouldn't have answered yes if you didn't want the install wizard to do it.

I always choose manual partitioning to avoid another "wizard" messing things up.  I am my computer's wizard!

---

### Post by mcduck on 2009-10-27
> **shram said:**
> The alternate install method wrote to the partition table of my second hardrive after asking it to use /dev/sdb1  for /var/cache/apt/archives.
I don't think this drive's partition table should have been written to with no boot element being used on data drive.

was /dev/sdb1 already formatted in some Linux filesystem and did you tell the installer to format it or not?

If the partition was formatted during the process then writing into partition table was correct behavior.

---

