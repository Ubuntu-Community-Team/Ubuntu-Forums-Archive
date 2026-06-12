---
title: "Failure when trying to install libmagick9-dev"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by modulaaron on 2010-03-17
I need to install the libmagick9-dev packages and am getting a failure when trying to do so:

```
apt-get install libmagick9-dev --fix-missing
```The failure message is as follows:

```
Err http://us.archive.ubuntu.com hardy-updates/main libpng12-dev 1.2.15~beta5-3ubuntu0.1
  404 Not Found [IP: 91.189.88.30 80]
Err http://security.ubuntu.com hardy-security/main libpng12-dev 1.2.15~beta5-3ubuntu0.1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.15~beta5-3ubuntu0.1_i386.deb  404 Not Found [IP: 91.189.88.31 80]
```Did this get moved to a different repository? If so, where can I find it now? If not, any idea on how I can get this working?

I am running Ubuntu 8.04 (Hardy) Server.

Thanks.

---

### Post by modulaaron on 2010-03-17
Looks like things are changing quickly. I just updated yesterday, but running:

```
apt-get update
```again today solved the problem.

---

