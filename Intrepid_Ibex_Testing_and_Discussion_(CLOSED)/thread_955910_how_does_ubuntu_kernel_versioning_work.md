---
title: "how does ubuntu kernel versioning work?"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by syko21 on 2008-10-22
In older versions kernel updates were accompanied by a 2.6.XX-+1 version system but after several updates the intrepid kernel is still at 2.6.27-7 is this the new way to do things or was the older way for a specific type of kernel rebuild?

---

### Post by PinkFloyd102489 on 2008-10-22
They're probably just patching things in it without making major changes to it.

---

### Post by wgrant on 2008-10-22
The kernel packages have a version in the name like '2.6.27-7'. The first part (2.6.27) is the upstream kernel version, and the last bit (7) is the ABI version. Only certain types of changes require an ABI bump.

The actual version of the kernel packages is something like 2.6.27-7.13, where 13 is the sequence number of the upload.

---

### Post by jfernyhough on 2008-10-22
Is there a(n easy) way to tell how the current kernel relates to the official? 2.6.27.3 has just been released.

---

