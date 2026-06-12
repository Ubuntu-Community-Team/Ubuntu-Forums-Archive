---
title: "Ubuntu 11.04 with Asus 1001p (or other computers with Atheros based wireless)"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by mdeneen on 2011-04-29
I had assumed that this was a Unity problem, but I finally figured out what was locking up my netbook.  At login, the wireless interface is configured.  Unfortunately, with the kernel module in 11.04, this causes some sort of kernel panic followed by a crash.

I attempted to gather a stack trace, but the file system never had anything of interest in /var/log/syslog because it crashes before it can flush / sync the log.

Anyway, here is the bug report:
[https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/762496](https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/762496)

And, if you install the pre-proposed kernel from the following ppa over a wired connection, you can get your wireless back.
[https://launchpad.net/~kernel-ppa/+archive/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/pre-proposed)

---

### Post by cullio on 2011-04-30
I have the same problem on my Asus 1001p ...

---

### Post by medoix on 2011-04-30
above link to update kernel from the proposed ppa works and fixed all issues on my 1000HE as well.

I was having boot up Unity issues as well as the WiFi lockup.

---

