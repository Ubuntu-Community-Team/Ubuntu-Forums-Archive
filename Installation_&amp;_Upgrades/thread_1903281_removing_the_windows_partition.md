---
title: "removing the windows partition"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by natestokely on 2012-01-02
I installed ubuntu using wubi to make sure it would work with all of my hardware, and now I want to remove the windows partition. I tried using the disk utility and gparted, and when I unmount the windows partition, the system crashes. Is it possible to remove the windows partition? If so, how? Thanks.

---

### Post by westie457 on 2012-01-02
Hi welcome to the Forum.

You cannot remove the Windows partition because you have a Wubi installation. The wubi installation is a virtual file system in the Windows partition. The easy way to remove the Windows partition is to do a full install and at the 'Where to install' screen choose the option to wipe the Hard drive. After that everything is done automatically apart from setting up the first user account.

---

