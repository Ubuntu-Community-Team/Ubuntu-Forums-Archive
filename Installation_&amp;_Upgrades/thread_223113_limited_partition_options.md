---
title: "limited partition options"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by sdahlin on 2006-07-25
I am attempting to install Ubuntu 6.06 on a laptop that already has a Win NTFS partition on it.  I want Windows to remain but the selection process wants me to include that partition in the Ubuntu install.  Is there a way to indicate to Ubuntu in the install process to give me the option to not include the Win partition?

---

### Post by aysiu on 2006-07-25
You need to use the Alternate CD for that. The Desktop CD forces you to mount all partitions.

After the installation, you can always delete the partition from the /etc/fstab list of partitions to automount.

---

