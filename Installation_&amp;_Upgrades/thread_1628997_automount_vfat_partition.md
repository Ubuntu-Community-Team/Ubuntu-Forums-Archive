---
title: "automount vfat partition"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by ampetrosillo on 2010-11-23
Hi everyone,

I have a dual-boot system, with Windows 7 and Ubuntu 10.10. I've made a "common" data partition in vfat, which I'd like to automount every time I boot into Ubuntu (as I have all my music collection and my Dropbox folder on there).

So I added the partition's UUID in /etc/fstab, I configured everything to point to /media/data, so far, so good.

But there is a little problem: whenever I try to delete files, I can't move them to the Trash, but I'm forced to delete them permanently each time. A relatively minor annoyance, but I'd like to solve this problem as well :)

Any ideas? I tried to change ownership of the partition, but it isn't possible, I think because vfat has no support for file ownership, right?

---

### Post by ampetrosillo on 2010-11-24
bump!

---

