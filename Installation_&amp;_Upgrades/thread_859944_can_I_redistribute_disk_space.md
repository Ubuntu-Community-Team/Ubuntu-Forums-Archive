---
title: "can I redistribute disk space ?"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by bobdobbs on 2008-07-15
Hi All.

I'm using Heron.

I was a little thoughtless when I was installing, and now the effects are showing.

On my 300Gb disk, I've only got about 1Gb spare to install applications,
and about 140Gb in my home dir.

Is it possible in any (fairly safe way) to redistribute available disk space?

I'm using a single physical disk. 'df' returns:

/dev/sda1             9.3G  7.8G  1.1G  89% /
varrun               1014M  212K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   52K 1014M   1% /dev
devshm               1014M  784K 1013M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda4             268G  115G  140G  46% /home
/dev/sda2              19G  780M   17G   5% /usr/local
gvfs-fuse-daemon      9.3G  7.8G  1.1G  89% /home/mantispalm/.gvfs

---

### Post by cdtech on 2008-07-15
Sure, just use the gparted live cd and you should be good to go.

---

