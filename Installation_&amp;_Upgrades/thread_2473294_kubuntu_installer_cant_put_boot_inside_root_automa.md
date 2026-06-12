---
title: "kubuntu installer cant put boot inside root automatically"
date: 2022-03-31
forum: Installation &amp; Upgrades
---

### Post by uv0 on 2022-03-31
installation stuck at "saving installed packages" ?
I am installing kubuntu 20.04, when i make only root, home and swap  partition somehow installer cant detect place to put data to installed  packages and get stuck  at saving installed packages.
on new install try to make own new partition  (ubuntu (auto)) and installs system in it and not in /  .
 But when i make separate boot partition there is currently no problem  ,installation goes well, but all new installations recommend /boot  inside the /
 to currently avoid for future "Boot out of space" i have allocated boot 1Gb. what shall i do?

---

### Post by TheFu on 2022-03-31
Which file systems are being used?
Any LVM, ZFS or encryption?

---

