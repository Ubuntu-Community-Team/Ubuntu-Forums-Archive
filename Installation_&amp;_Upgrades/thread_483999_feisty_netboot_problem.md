---
title: "feisty netboot problem"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by bartzitz on 2007-06-25
hello,

i've installed PXE infrastructure and NFS share to network boot feisty. it boots fine, mounts squashfs filesystem and starts to launch init.d/* scripts from there, then it breaks:

* Checking filesystems...
mkdir: Cannot create directory '/dev/shm/var.run'
...
mount: Mounting /var/run on /dev/shm/var.run failed: No such file or directory
...
* Mounting local filesystems...
mount: Mounting tmpfs on /tmp failed

i guess it's something related to unionfs stuff, but not sure. how can i fix and debug it?

---

