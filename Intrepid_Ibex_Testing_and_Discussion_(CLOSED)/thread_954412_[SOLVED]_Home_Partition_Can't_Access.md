---
title: "[SOLVED] Home Partition Can't Access"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-10-21
The Lost+Found when I click on it says that "You do not have the permissions necessary to view the contents of "lost+found"."   My home partition is only 24 GB out (40 GB Hard Drive.)   7.4 GB are unable to be accessed by me, the sole user of this machine.  

What can I do to get back the locked partition?

---

### Post by philinux on 2008-10-21
That folder in Home, not your home folder, is owned by root in a default install.

I would think gksudo nautilus would be the best then you can explore it. You could change the permissions as it's a sole use pc.

---

### Post by Sef on 2008-10-21
Thank you.  That worked.

---

### Post by jfernyhough on 2008-10-21
IIRC, Ext2/3 reserves 5% of the partition so that the root user can always log on. This might be the cause of the 'problem'.

---

