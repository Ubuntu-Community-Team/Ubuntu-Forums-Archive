---
title: "ZFS volumes Solaris or Ubuntu"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2009-12-23
I want to know is there some thing equivalent to ZFS volumes on Ubuntu some tutorials or links that can let me know about ZFS volumes.

---

### Post by shredswithpiks on 2009-12-23
[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)
[http://www.wizy.org/wiki/ZFS_on_FUSE](http://www.wizy.org/wiki/ZFS_on_FUSE)

Basically ZFS run in userspace the way ntfs-3g works. It works ok, I can't comment on performance since I've only played around with it in virtualbox on my laptop (ext4 writes at 8megs/second, zfs writes at 6megs/second... far from a scientific study but that's what I got).

In the future we should have btrfs out of development and ready for proper use. Check out [http://btrfs.wiki.kernel.org](http://btrfs.wiki.kernel.org) for more info.

---

### Post by tapas_mishra on 2009-12-23
Ok I have checked all the links.Thanks

---

