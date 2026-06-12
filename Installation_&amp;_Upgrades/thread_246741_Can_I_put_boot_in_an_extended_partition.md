---
title: "Can I put /boot in an extended partition?"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by Burke on 2006-08-29
Can I put /boot in an extended partition?

If I move my boot partition, will my system die?

Thanks

---

### Post by mlind on 2006-08-30
> **Burke said:**
> Can I put /boot in an extended partition?

If I move my boot partition, will my system die?

Thanks

GRUB supports booting from extended partition, so yes you can.

If you move /boot contents to separate partition, you need to edit /boot/grub/menu.lst and correct **# groot=** to point the new /boot partition.
After this you need to run **update-grub** script, so that automagic kernel entries are updated to use the new /boot partition.

---

### Post by Burke on 2006-09-01
OK, I solved my problem, thanks for the help

---

