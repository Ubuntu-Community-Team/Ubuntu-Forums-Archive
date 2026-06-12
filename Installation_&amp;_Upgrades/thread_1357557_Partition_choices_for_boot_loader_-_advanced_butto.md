---
title: "Partition choices for boot loader - advanced button"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by tompfr on 2009-12-17
This question applies to at least the last 2 releases (9.04 and 9.10):

On the Ready to Install screen, when choosing the Advanced button, it then shows the choices of where to install the Grub boot loader.

That's fine, but in addition to the predictable choices like /dev/sda1, /dev/sda2, etc., it also lists /dev/sda-1, /dev/sdb-1, etc. These look to me like they represent free space (unpartitioned) areas on the drive. 

The question is: WHY are choices with the hypen (eg /dev/sda-1) listed at all, since the goal is to install the boot loader to a partition boot sector when you choose the Advanced button. 

Will appreciate the answer if anyone knows why this is done.

---

### Post by dandnsmith on 2009-12-17
I don't know the answer - but I can give you some idea of what it isn't: when I installed, a day or two ago, I wasn't given any choices relating to the unallocated spaces on my HDDs.

---

### Post by tompfr on 2009-12-17
> **dandnsmith said:**
> I don't know the answer - but I can give you some idea of what it isn't: when I installed, a day or two ago, I wasn't given any choices relating to the unallocated spaces on my HDDs.

Thanks, that adds to the mystery. 

Others have seen the hyphened choices also, and asked me about it. I'm still at a loss to explain it, so thought I'd ask here.

---

