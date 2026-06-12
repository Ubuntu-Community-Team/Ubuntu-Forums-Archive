---
title: "/boot vs root partition"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by mailforbiz on 2006-05-22
Hi

Sorry if this is a rather basic question - what is the difference between the /boot and / ? Is there a reason to have both ? What would be the recommended sizes for about 28 Gig space (I'm planning to keep about half of that in /home).

Thanks in advance.

---

### Post by aysiu on 2006-05-22
I've never seen a convincing case for a separate /boot partition.

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by Sef on 2006-05-23
>  I've never seen a convincing case for a separate /boot partition.

There is a case.  If you are installing XFS or JFS, then you need to have a separate boot partition or your GRUB will fail to install.  That's what it took to get Ubuntu and XFS together.

---

