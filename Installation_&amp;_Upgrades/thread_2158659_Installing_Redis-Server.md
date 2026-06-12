---
title: "Installing Redis-Server"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by parkerj on 2013-06-30
I am using Ubuntu 10.04, and I am trying to install redis-server, however, I keep getting this error message:

```
Writing extended state information... Done(Reading database ... 182289 files and directories currently installed.)
Unpacking redis-server-2.2.4 (from .../redis-server-2.2.4_0127-1ubuntu25_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/redis-server-2.2.4_0127-1ubuntu25_amd64.deb (--unpack):
 trying to overwrite '/etc/logrotate.d/redis-server', which is also in package redis-server 2:2.2.12-1ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

So, what I did is rename log rotate to /etc/logrotate.d/redis-server.backup, but after doing that, I still get the same error message. Any help with this is greatly appreciated.

---

