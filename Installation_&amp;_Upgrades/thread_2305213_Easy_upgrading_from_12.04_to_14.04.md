---
title: "Easy upgrading from 12.04 to 14.04"
date: 2015-12-03
forum: Installation &amp; Upgrades
---

### Post by vivienneanthony on 2015-12-03
Hello,

I'm installing a new SSD on my computer from 64GB to 250GB. All my important information I placed on a separated HD.

The question is, I want to just take out the old SSD install the new SSD and do a fresh Ubuntu 14.04 install. Since all the data files software is on the physical HDD.
What other things I need to do other tthen mounting the non-SSD hard drive partitions.

Actually both drives already is Ext4.

Vivienne

---

### Post by blm-ubunet on 2015-12-03
Almost nothing.. you can always re-connect it & auto mount into /media folder to search for some obscure config file.
SATA drives are hot pluggable, scary as that seems..


Only thing I would consider is the mount-point setup of the /home folder.

By default /home is mounted in the root / filesystem but it is a good idea to mount /home as a separate partition.
But if you already have your personal stuff on a separate HDD then maybe there is little benefit in that scheme.
If you do separate /home you have to estimate approp. partition sizes..

You might want to take a snapshot (copy) of "/etc/fstab" as a guide to re-instating the mount-point of your HDD but be aware that some of the UUIDs identifiers will change (new formatted partition has a new UUID). Your HDD should have the same UUID.

This lists all your mounted partitions UUID details.
```
sudo blkid
```

---

