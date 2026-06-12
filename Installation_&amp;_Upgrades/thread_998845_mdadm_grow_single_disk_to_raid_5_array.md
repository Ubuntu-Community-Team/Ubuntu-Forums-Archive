---
title: "mdadm grow single disk to raid 5 array?"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by khm on 2008-12-01
I have been searching around to find documentation on this, but haven't really found anything yet.

Does anyone know if it is possible to use mdadm to "grow" a raid 5 array starting from a single disk (obviously not raid at this point) to 3 other disks?

Thanks.

---

### Post by psusi on 2008-12-01
Yes, it can reshape the array.  See the mdadm man page.

I have never tried going up to raid 5, but I have started with a single disk raid1 then added the second drive.

---

