---
title: "iscsi paritions on Hardy"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by aspasiasf on 2008-04-28
Hello,

I noticed the following documented in the Release notes:

iSCSI partitions

    * The open-iscsi package is now a maintained option in Ubuntu 8.04 LTS, and iSCSI NAS partitions can be configured right from the installer. At this time, however, the root and boot filesystems should be placed on a local partition.

Just to clarify:

1.  Currently iscsi-root booting is not supported?

I tried to check the etc/initramfs-tools/initramfs.conf if there is a new option to boot off an iscsi drive;  but seems like still the same, only nfs boot ...

please confirm that this is so?

2.  Has anyone attempted to configure iscsi root PXE booting on Ubuntu, if so any advise on how to prepare the disk image?

I appreciate any feedback and/or response.

tia,

aspasia.

---

