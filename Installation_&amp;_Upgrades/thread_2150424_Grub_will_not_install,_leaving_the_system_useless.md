---
title: "Grub will not install, leaving the system useless"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by justmakeitwork on 2013-06-01
On a Dell Poweredge 850, 4GB memory using a single SATA 1.5 TB disk, Ubuntu 12.04.2 LTS both server and desktop versions (64 bit) and 13.04 desktop (64-bit) create a paradox where grub cannot install as the final installation step. I let the system use the entire disk and when grub tries to install on /dev/sda it results in FATAL ERROR (with no other explanation.) Trying to install on /dev/sda1, /dev/sda2 and even /dev/sda5 also fails in the same way. Next, if I try to lay the system out manually, leaving 1MB unused on sda1 as space for grub, the system seems not to know where to install and runs out of space (versus 1300 GB free space on a partition set for use by '/'.) Therefore I cannot produce a running Ubuntu system. USEFUL TO KNOW: I can install laptop version 10.10 on the same system with NO GRUB COMPLAINTS and the system boots fine.

---

### Post by justmakeitwork on 2013-06-01
I can't delete this post.

---

