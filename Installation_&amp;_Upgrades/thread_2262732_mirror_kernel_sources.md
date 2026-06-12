---
title: "mirror kernel sources"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by gobo7 on 2015-01-26
i've built a ubuntu 14.04 mirror on a portable drive.  all of the deb lines are for binaries.  there are a couple of machines that run vmware workstation  and therefore need kernel sources.    what is the correct deb-src line that would pull down kernel sources? i've tried several without success.     my best guess for mirror.list:  ```
 deb-src http://us.archive.ubuntu.com/ubuntu trusty main restricted universe multiverse 
```    for sources.list:  ```
 deb-src file:///media/user/repos/ubuntu1404/mirror/us.archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse 
```     thanks.

---

### Post by gobo7 on 2015-01-31
i guess i didn't ask this correctly.
[br]1[/br]
i have 14.04 mirrored on a local drive.  when i try to run
```

apt-get source linux-image-$(uname -r)

```
i get a bunch of file not found and failed to fetch for linux_3.13.0 named files.  that leads me to believe i have something missing from my mirrors.list.  but i may be wrong.
[br]1[/br]
can anyone suggest what i'm missing?

---

