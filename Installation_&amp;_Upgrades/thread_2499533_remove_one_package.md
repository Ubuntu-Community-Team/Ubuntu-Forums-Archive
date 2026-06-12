---
title: "remove one package"
date: 2024-07-30
forum: Installation &amp; Upgrades
---

### Post by apgp on 2024-07-30
Ubuntu 24.04 installation problem
After installing the distro from Ubuntu 22.04 I cannot update packages because it does not allow me to remove linux-image-5.15.0-117-generic. 
This message returns to me: 
dpkg: error processing package linux-image-5.15.0-117-generic (--remove):
thread installed package linux-image-5.15.0-117-generic post-removal script returned error exit code 127. Can you help me remove that package?

---

### Post by ubfan1 on 2024-07-30
24.04 or 22.04?  Sometimes the package manager purge/remove fails if all the expected pieces are not present.  The error message should indicate what's missing and causing the problem.  Usually, it is sufficient to simply make an empty file that the package manager wants to see (sudo touch /path/file), and the  remove then succeeds.

---

