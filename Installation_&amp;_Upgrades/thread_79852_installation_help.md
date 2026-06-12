---
title: "installation help"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by jiggyup on 2005-10-21
hi,

i just recently installed breezy on a dual partition with xp. everything seems to be working fine but im getting errors when i try to install something.

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_b inary-i386_Packages) - stat (2 No such file or directory)

what can i do to fix this problem?

---

### Post by aysiu on 2005-10-21
Try this ```
sudo nano /etc/apt/sources.list
``` Put a # sign in front of the first line.
Control-X
y
Enter
```
sudo apt-get update
```

---

### Post by jiggyup on 2005-10-21
hi aysiu thanks for the help it solved it right away

---

