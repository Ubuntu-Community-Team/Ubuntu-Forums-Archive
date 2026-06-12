---
title: "Unable to enable swap in 15.04"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by drew37 on 2015-12-14
I am running a fresh install of Ubuntu MATE 15.10* (typo'd the thread title), I chose to encrypt my home folder during the installation and have been running into my Swap space no longer being active. Attempting to un-comment swap section in my /etc/fstab results in having to enter my password for every installation during a software update etc. I then discovered this has been an issue and Ubuntu auto comments it out to avoid this.

However, I found this fix: [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875)

When getting to the 'sudo mkswap -U UUID /dev/sda3' I continuously receive a "Resource busy" error, if I attempt a Swapon from either Gparted or command line I also receive an error.

Attempting 'sudo umount /dev/sda3' to potentially run the mkswap command also results as the partition not being mounted.

Any ideas?

Thanks!

---

