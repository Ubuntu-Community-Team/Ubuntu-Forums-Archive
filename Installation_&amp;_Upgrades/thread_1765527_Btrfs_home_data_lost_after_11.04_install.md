---
title: "Btrfs /home data lost after 11.04 install"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by StTwister on 2011-05-23
Hi,

I did a fresh install of Ubuntu 11.04. I had / mounted on a ext4 partition and /home on a btrfs partition. I choose to format and reinstall over /, but keep /home on my old btrfs partition without formatting it.

However, everything on /home seems to be lost now. I have a subvolume called @home which looks like a brand new /home directory and that seems to be all.

btrfs filesystem show tells that there's still 47 GB used in the partition. Is the old data lost? Is there anyway I can recover it?


I did this before with /home mounted on a ext4 partition instead of btrfs, and no data was lost.


Thanks!


EDIT: solved [https://bugs.launchpad.net/ubuntu-release-notes/+bug/771188](https://bugs.launchpad.net/ubuntu-release-notes/+bug/771188)

---

