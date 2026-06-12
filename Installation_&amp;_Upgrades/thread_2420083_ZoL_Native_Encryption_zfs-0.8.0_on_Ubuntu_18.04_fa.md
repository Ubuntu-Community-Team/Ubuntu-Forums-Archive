---
title: "ZoL Native Encryption zfs-0.8.0 on Ubuntu 18.04 fails 'zpool create'"
date: 2019-05-30
forum: Installation &amp; Upgrades
---

### Post by brotherbeijing on 2019-05-30
after installing from [https://launchpad.net/~jonathonf/+archive/ubuntu/zfs-debian](https://launchpad.net/~jonathonf/+archive/ubuntu/zfs-debian) on ubuntu 18.04 i tried to do
```
$ truncate -s 1G /root/block
$ zpool create testpool /root/block
```

and it fails

works o.k. if using the 18.04 default zfsutils-linux package

---

### Post by TheFu on 2019-05-30
Well, the description of that PPA is "cutting edge" ... which I would translate to "bleeding edge".  If you need stability, use the default packages provided by Canonical.

I bet Jonathon would appreciate knowing about the issue. [https://bugs.launchpad.net/~jonathonf](https://bugs.launchpad.net/~jonathonf)

---

### Post by brotherbeijing on 2019-05-30
The PPA has a 16.04 version of zfsutils-linux

I'll try that next

...

---

### Post by jonathonf on 2019-06-30
> **TheFu said:**
> I bet Jonathon would appreciate knowing about the issue. [https://bugs.launchpad.net/~jonathonf](https://bugs.launchpad.net/~jonathonf)

Yes I would.

Also 0.8.1 is available now.

---

