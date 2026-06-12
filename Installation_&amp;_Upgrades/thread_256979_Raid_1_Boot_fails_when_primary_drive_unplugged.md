---
title: "Raid 1 Boot fails when primary drive unplugged"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by PatrickC on 2006-09-13
I'm building a amd64 server where I want to use Raid 1 for hard disk redundancy. Everything seems to work fine with one exception. When I test booting the system with the primary (sda) drive unplugged the system just hangs. If I try the same test with sdb unplugged the system comes up and sees the second raid drive is missing and continues to work.

Is GRUB only installed on the primary drive? It is almost like there is nothing to boot the system on sdb. The raid partitions were all set up during the install.

Thanks,
Patrick

---

