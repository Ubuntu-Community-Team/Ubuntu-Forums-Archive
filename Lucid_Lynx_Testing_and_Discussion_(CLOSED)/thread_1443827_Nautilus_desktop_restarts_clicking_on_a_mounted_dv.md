---
title: "Nautilus desktop restarts clicking on a mounted dvice"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Macchia on 2010-03-31
When i click on a pendrive or my raid1 placed on the desktop, nautilus restarts, reporting this on .xsession-errors:
```

/home/mike/.themes/paysages/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/mike/.themes/paysages/gtk-2.0/gtkrc:108: Murrine configuration option "profile" is no longer supported and will be ignored.
Initializing nautilus-gdu extension

```

This happens from 2 or 3 days ago, maybe after an upgrade.

---

### Post by Macchia on 2010-03-31
it happens only to me? anyone can help me find out what's wrong?

---

### Post by Killigrew on 2010-04-03
Hi

Can you access Network shares?
I Had a problem similar or identical problem
which was caused by nautilus-actions.
If you have it installed, try if a temporary deletion helps.

greetings :)

---

### Post by Macchia on 2010-04-07
Thanks, using nautilus-action-config-tool removed the mount/umount disk image files and the problem is gone.

---

