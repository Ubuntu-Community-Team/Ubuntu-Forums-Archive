---
title: "Install 10.10 with btrfs compressed root partition"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Bigsy on 2011-01-22
I have a netbook with a small ssd so would like to install 10.10 desktop with btrfs compression enabled, preferably the new lzo compression option.

I can obviously install on btrfs partition but there seems to be no way to add compression, only adding it to fstab after install which means all the OS files are not compressed.

Whats the best way to go about this? I searched the site but couldn't find a solution.

Thanks.

---

### Post by dabl on 2011-01-22
The btrfs compression option requires kernel 2.6.37 or later, if I remember correctly.  So you'd have to install a daily build of 11.04 to get that.

[http://www.phoronix.com/scan.php?page=article&item=btrfs_space_cache&num=1](http://www.phoronix.com/scan.php?page=article&item=btrfs_space_cache&num=1)

---

### Post by msktje on 2011-01-28
take a look at this:

[http://askubuntu.com/questions/6197/trick-installer-to-use-btrfs-root-with-compression](http://askubuntu.com/questions/6197/trick-installer-to-use-btrfs-root-with-compression)

If it works is it possible to elaborate more on how you did it?

---

