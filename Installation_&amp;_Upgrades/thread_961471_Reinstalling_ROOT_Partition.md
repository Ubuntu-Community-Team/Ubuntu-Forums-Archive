---
title: "Reinstalling ROOT Partition"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by attaeam on 2008-10-28
Hey, so as of right now I am extremely new to Linux but very eager to learn. I am at college right now but before I left my brother set up a dual hard disk running Visa and Ubuntu 8.04. He also separated my root, swap, and home partitions, and he also gave me an Ubuntu Live CD if I were to ever run into any problem. Right now I would like to reinstall my root partition, the only problem is I am not entirely sure where/what my root partition is, and how to go about it. Any help would be greatly appreciated.

I hope I explained everything in a way that is not too confusing.
Thanks!
:]

---

### Post by Amarsingh0793 on 2008-10-28
Why do you want to reinstall the root partition?

---

### Post by Settler on 2008-10-28
You can simply re-install Ubuntu. 

Just don't forget to:

1. Set/Redefine partition again without deleting them. e.g. /root again with ext3 etc etc swap and home.
2. Select root partition to be formatted.
3. Be carefull not to format the /home partition.
4. If you delete and re-create the partitions they will be formatted so don't delete them. Just format the / partition.

---

