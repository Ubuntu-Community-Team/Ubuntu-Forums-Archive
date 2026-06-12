---
title: "Bug fixed upstream, how to make sure it lands in Lucid?"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-03-03
GParted had problems with cloning larger NTFS partitions, this got fixed in Gnome git and should be included in version 0.5.2. 

As this seems to be a common use case, I wonder how to make sure the fix finds its way into Lucid (either by including GParted 0.5.2 if released in time, or by applying that specific patch)?

---

### Post by ikt on 2010-03-03
[https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess)

?

---

### Post by 23meg on 2010-03-03
Are there bug reports on the issues in the Ubuntu bug tracker? If so, take a look at those and see if they've been closed with a cherry-picked patch from upstream git already, or if that has been suggested. And take a look at the Ubuntu changelog for gparted too.

In any case, you'll want to look at [https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess), and file a bug report quoting the relevant upstream changelog entry to explain the rationale.

---

### Post by MacUntu on 2010-03-03
Nope, the bug isn't in LP and the patch definitely not already cherry-picked and applied. Thanks for those links, though. :)

---

