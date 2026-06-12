---
title: "Mount a Partition"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by fred0843 on 2008-05-08
Installed Ubuntu 8.04.I want to mount a Partition (sdb12) to automount and share on my network.I tried pysdm,but will not work for Partition higher then 9.Can I just edit my fstab file to do the same thing.

---

### Post by lemming465 on 2008-05-10
Yes, you can manually edit fstab to add more automatic mounts.  In your case something like: */dev/sda12 /your/mount/point ext3 defaults 0 2* if it was formatted as ext3.

Sharing it out is a separate issue, using NFS or Samba or something.

---

