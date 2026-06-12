---
title: "Accessing my slave hard drive"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by philipluna66 on 2008-04-06
When I click on computer and then on my slave hard drive I get error message error: device /dev/hdb1 is not removable

error: could not execute pmount
How do I correct the proble??? THANKS

---

### Post by logos34 on 2008-04-06
try adding the drive to /etc/fstab.

If it's an NTFS partition, use ntfs-config:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

ext3:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

