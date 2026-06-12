---
title: "Dual Boot 6.06 (Dapper) *and* 8.04 (Hardy) - Possible?"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2008-09-26
Is it possible to dual boot both Ubuntu 6.06 (Dapper) *and* Unbuntu 8.04 (Hardy)?

If so, what do I specify in the partitioner which currently lets me specify only one root partition ('/'). 

I mean, I first run the Ubuntu 8.04 installer. It goes through the partitioner. I would like to allocate up front the space for the 6.06 stuff as well. But if I add another root partition for the 6.06, won't that confuse the 8.04 installer?

Thanks,
Alex

---

### Post by dstew on 2008-09-26
You should be able to do this. For example, create three partitions using gparted before you start the installation. The first two will be the root partitions for the two systems, and the last will be a shared swap partition. If your two partitions for root are, say, /dev/sda1 and /dev/sda2, just specify /dev/sda1 to have the mount point '/' when you install 6.06, and specify /dev/sda2 to have the mount point '/' when you install 8.04. Specify /dev/sda3 to use as swap for both installations. When you install grub at the end of the 8.04 installation, the grub installer should recognize your 6.06 installation and make a menu item for it.

---

