---
title: "merge /dev, /dev/shm, /var/run, /var/lock partitions to /"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by Shreshtha on 2010-06-27
Result of df -h is following

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              16G  9.3G  5.6G  63% /
udev                  1.6G  304K  1.6G   1% /dev
none                  1.6G  540K  1.6G   1% /dev/shm
none                  1.6G  352K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw

Except first, all others are unused. How can I merge them to /dev/sda8 i.e. root?

---

