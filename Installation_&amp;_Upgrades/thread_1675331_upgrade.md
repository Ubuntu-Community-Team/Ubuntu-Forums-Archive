---
title: "upgrade"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by mark1969 on 2011-01-25
Hi all,

I have a separate home partition which I encrypted during installation. When I installed meerkatat I formatted the root partition and used the existing /home partition without formatting as I usually do. This time it wouldn't mount the /home partition. I assume this is because of the encryption.

My question is,  How do I install a new distro using an existing home partition with an encrypted home folder?

---

### Post by zvacet on 2011-01-29
Of course you will not format your home partition,but you have to give it mount point during installation.So,in short just mark that partition as home and do not format it.When installation is finished that partition will be mounted on boot.

---

