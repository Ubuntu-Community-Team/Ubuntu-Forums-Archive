---
title: "chroot issue"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by gdelta9 on 2008-07-01
Hello,
im trying to use chroot to install a package using live cd to my kubuntu installed system.
i do what is indicated in an ubuntu how to.In moe detail i do this:

```

cd /
sudo -s -H
  mount -t ext3 /dev/sda2 /mnt
  mount -t proc proc /mnt/proc
  mount -t sysfs sys /mnt/sys
  mount -o bind /dev /mnt/dev
  chroot /mnt  /bin/bash

```

And then when i run 

```

apt-get install sysv-rc

```

i get this error

```

dpkg: `update-rc.d' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Any ideas how to overcome this?
Thnx a lot in advance!!!!

---

