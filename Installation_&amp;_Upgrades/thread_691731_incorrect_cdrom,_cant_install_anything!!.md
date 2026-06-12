---
title: "incorrect cdrom, cant install anything!!"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by toucansam99 on 2008-02-08
For some reason ubuntu puts the cdrom at /media/cdrom1 instead of /media/cdrom0 so I can't install anything because it always uses the /cdrom alias which points to /media/cdrom0.  and /media/cdrom0 is blank.  :confused:

---

### Post by zvacet on 2008-02-09
```
sudo gedit /etc/fstab
```

see if cdrom line look like this one

> /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

If not change it.You can maske backup of your fstab first.Just in case.

---

