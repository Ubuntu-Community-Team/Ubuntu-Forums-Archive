---
title: "A problem with installing 6.10 RC"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by yjsyj on 2006-10-23
I tried to install 6.10 RC today, but when I reached to step 5 (prepare mount point), I chosed to mount a 5G partition as my "/" and a 13G partition as my "/home", and I got this error: No root file system. My 5G partition is a Primary partition on my second hard drive(hdb2) and the 13G partition is a logical partition(hdb5). Both of them are formated as reiserfs format.
:confused: 

I tried to reinstall 6.06 LTS with the same mount point and got no error. Dose anybody know why would this happen and how to fix it?

Thanks a lot.

---

### Post by kerry_s on 2006-10-23
I think the installer is still abit buggy it took me 3 tries to get a good working install.

---

