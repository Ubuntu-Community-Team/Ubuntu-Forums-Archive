---
title: "filesystem creation failure during installation"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by mzycdth on 2011-07-18
Hi everyone, 

I'm trying to install ubuntu on an external drive. During installation I initially had an error with /dev/sdb being mounted to /cdrom. Sorted that and now installation initiates.

Shortly afterwards it fails with the error:

"The ext4 file system creation in partition #1 of SCSI5 (0,0,0) (sdb) failed."

I'm installing to the target drive from a live install on that same drive. Partition 1 currently contains the live OS. Is this the issue?

"/" mount point  is /dev/mapper/vg-root (230gb) and is encrypted with encryptsetup luksFormat, "/boot" mount point is sdb1 (2gb). ubuntu live exists in sdb1.

Thanks in advance

---

