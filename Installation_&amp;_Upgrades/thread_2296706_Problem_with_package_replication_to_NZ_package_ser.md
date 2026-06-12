---
title: "Problem with package replication to NZ package servers?"
date: 2015-09-28
forum: Installation &amp; Upgrades
---

### Post by dev23 on 2015-09-28
Hi,

I've noticed that my Ubuntu Server 14.0.4.3 LTS machines have stopped getting updates.

I get lots of 404 errors, such as the ones below. I thought maybe I had a problem with my sources, but I don't think so. I think it's a package replication problem. If I check the directories on [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) I can verify the files are indeed missing. But if I check [http://archive.ubuntu.com](http://archive.ubuntu.com) instead then I can see them. 

Example: [http://nz.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20.7_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20.7_amd64.deb) vs [http://archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20.7_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.20.1-5.1ubuntu20.7_amd64.deb)

Snippet of output from apt-get upgrade (after running an update):
```
Get:1 http://nz.archive.ubuntu.com/ubuntu/ trusty-updates/main e2fslibs amd64 1.42.9-3ubuntu1.3 [182 kB]
Get:2 http://nz.archive.ubuntu.com/ubuntu/ trusty-updates/main e2fsprogs amd64 1.42.9-3ubuntu1.3 [667 kB]
Err http://nz.archive.ubuntu.com/ubuntu/ trusty-updates/main mount amd64 2.20.1-5.1ubuntu20.7
  404  Not Found
Err http://nz.archive.ubuntu.com/ubuntu/ trusty-updates/main util-linux amd64 2.20.1-5.1ubuntu20.7
  404  Not Found
Err http://nz.archive.ubuntu.com/ubuntu/ trusty-updates/main bsdutils amd64 1:2.20.1-5.1ubuntu20.7
  404  Not Found
```

My sources are:
```

deb http://nz.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ trusty main restricted

deb http://nz.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

deb http://nz.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ trusty universe
deb http://nz.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ trusty-updates universe

deb http://nz.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

deb http://nz.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

```

Is there a way to report this?

---

### Post by dev23 on 2015-09-29
Anyone? I might just have to revert to the main servers.

---

### Post by wyaeld on 2015-09-30
Happening to me too

---

