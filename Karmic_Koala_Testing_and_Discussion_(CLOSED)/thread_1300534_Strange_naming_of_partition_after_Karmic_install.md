---
title: "Strange naming of partition after Karmic install"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by klemperal on 2009-10-25
After installing the Karmic beta, one of my partitions ended up with a strange name (see the attached screen shot).  In all my past installs of Ubuntu, this partition has been named "disk" within the /media folder.  Anyway I can change this manually to "disk?"

[ATTACH]133017[/ATTACH]

---

### Post by dearingj on 2009-10-25
Karmic names drives using unique identifiers (those seemingly random numbers and letters actually aren't random :) ) rather than the generic name 'disk', unless the partition has a label in which case that label is used. I think you can assign it a label using GParted or other partition management software.

---

### Post by lovinglinux on 2009-10-25
> **dearingj said:**
> I think you can assign it a label using GParted or other partition management software.

Yes you can, but Karmic comes with the new Disk Utility that allows you to change the Label easily.

---

### Post by philinux on 2009-10-25
> **lovinglinux said:**
> Yes you can, but Karmic comes with the new Disk Utility that allows you to change the Label easily.

+1. System>admin>Disk Utility.

---

