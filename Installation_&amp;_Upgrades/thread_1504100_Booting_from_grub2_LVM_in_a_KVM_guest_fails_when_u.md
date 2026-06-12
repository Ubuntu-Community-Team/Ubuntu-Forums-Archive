---
title: "Booting from grub2 LVM in a KVM guest fails when using the linux-virtual package"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by nutznboltz on 2010-06-07
Well it does.  I switched a working Lucid KVM guest from linux-server to linux-virtual and it could not mount root at boot time and issued a panic instead.  Switching back (booted from CD and used "rescue a broken system") revived the VM.

My first guess is that some DM driver module needed for LVM is missing from the linux-virtual package.

---

### Post by nutznboltz on 2010-06-07
Probably not a missing module.

With linux-image-server

CONFIG_BLK_DEV_DM=y

With linux-image-virtual

# CONFIG_BLK_DEV_HD is not set

---

### Post by nutznboltz on 2010-06-07
Similar to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560717](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560717)

---

