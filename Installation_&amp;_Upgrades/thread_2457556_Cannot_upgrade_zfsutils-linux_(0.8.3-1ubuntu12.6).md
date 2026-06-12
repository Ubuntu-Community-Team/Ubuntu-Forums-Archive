---
title: "Cannot upgrade zfsutils-linux (0.8.3-1ubuntu12.6)"
date: 2021-02-04
forum: Installation &amp; Upgrades
---

### Post by dmp1ce on 2021-02-04
I could use some suggestions on how to get my Ubuntu upgraded. I tried `sudo apt update && sudo apt upgrade` and got the following error in the screenshot attached.

I think it might be the same issue here: [https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1914146](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1914146)

How should I debug the issue so I can upgrade Ubuntu?

---

### Post by dmp1ce on 2021-02-05
I used this answer to solve my issue. [https://askubuntu.com/a/1231053/25776](https://askubuntu.com/a/1231053/25776)

Although, I needed to move the `/var/cache` directory to `/var/cache.old` and then `mount -a /var/cache` which seemed to do nothing. I then also created the `/var/cache` directory and used `rsync` to copy over as much data from `/var/cache.old` as I could.

After a reboot I was able to upgrade!

---

