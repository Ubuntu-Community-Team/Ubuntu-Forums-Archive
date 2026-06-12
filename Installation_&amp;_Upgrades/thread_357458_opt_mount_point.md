---
title: "/opt mount point"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by scruffydawg on 2007-02-09
I just switched to Ubuntu from Fedora and have a question about the "/opt" mount point: specifically, does Ubuntu use it?

In order to make my life easier, I decided to keep the partitions and mount points ("/", "/boot", "/usr", "/usr/local", "/home", "/var", "/tmp", and "/opt") as they were under the other distro, and just format and install into them. I looked at "/opt" and it appears to be empty (except for "lost+found") and was wondering if it was safe to remove (or reuse as something else)?

Thanks in advance.

John

---

### Post by bapoumba on 2007-02-10
Hi,
/opt is for optional packages. Some distros used to put KDE in there, I think (needs to be double-checked). Mine (in the / filesystem) is empty. Some people use it to put their compiled packages for ex.
Each partition has its lost+found to put rescued files after a crash or if fsck finds bad files.

As far as moving it back to /, I would say it's okay but you'll need to check how this can safely be done. Or may be resize it down ?

---

