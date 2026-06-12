---
title: "Using APTonCD"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by yair999 on 2007-12-11
I try to use APTonCD to copy packages installed on one PC to another PC with no Internet, however it relies on /var/cache/apt/archives which gets partially cleaned (after 30 days packages are deleted).

So I need to renew the deleted packages and I do it by:
sudo apt-get --download-only --reinstall install package_name

However this does not pull the dependencies.

I've asked at Kubunto forums (I run Kubuntu Gutsy) but they could not help, see here:
[http://kubuntuforums.net/forums/index.php?topic=3089393.0](http://kubuntuforums.net/forums/index.php?topic=3089393.0)

Any help I can get here?

Thanks,

Yair

---

### Post by yair999 on 2007-12-16
Well, I've found the currently ultimate solution here:

[http://ubuntuforums.org/showthread.php?t=572819&page=2](http://ubuntuforums.org/showthread.php?t=572819&page=2)

---

