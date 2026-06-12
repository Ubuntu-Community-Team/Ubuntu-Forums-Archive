---
title: "WARNING: nfs-user-server  for booting diskless systems"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by janaka on 2008-10-28
Gday,
I was trying to use a NFS export as a root file system for a diskless system.  The NFS server I used was the Ubuntu(8.04) **nfs-user-server**.  I was getting the following write failure in the init script:
```
cannot create /etc/mtab: Invalid argument
```

I knew it was a file access/locking issue but didn't know where it was coming from.  After much investigation and frustration :confused: I worked it out that the NFS server was buggered (to put it mildly).
It turns out that this server does not handle file locking properly (more info at /usr/share/doc/nfs-user-server/README.CDF).
In my 'humble' opinion  there should have been a big WARNING on this package description :mad: .

I uninstalled **nfs-user-server** and installed **nfs-kernel-server** instead and everything works happily :).

Hopefully someone else will find this useful.

Cheers (after some frustration)
  Janaka

---

