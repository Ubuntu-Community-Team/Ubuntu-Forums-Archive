---
title: "Solution for kernel panic!"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Kognit on 2010-04-11
One week ago i installed ubuntu 9.10 through WUBI. Everything worked fine until someday when booting on the screen appeared this message: ```
Kernel-panic - not syncing : VFS : Unable to mount root fs on unknown-block(0,6)
```

After research i found that it was the file "wubildr" on hard drive c: that makes problem. In this link [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) download the copy of this file and overwrite the "wubildr" file on your c: disk.

More on the issue in this link [http://narenbharatwaj.blogspot.com/2010/01/solution-for-kernel-panic-in-ubuntu-910.html]("http://narenbharatwaj.blogspot.com/2010/01/solution-for-kernel-panic-in-ubuntu-910.html"). Thank you Naren Bharatway

---

