---
title: "updating on USB live installation"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by mma8x on 2010-02-05
i'm using kubuntu karmic on a 2 gig usb drive.  upon first installation, i have about 1.1g free.  however, when i try to upgrade the packages, all of the free space is taken up.  if i try to remove all uneeded packages, i can manage about 100 mb of free space.  so 1 gig is sucked up by the upgrades, which doesn't seem right.
a little more info:
```
ubuntu@ubuntu:/$ sudo du -h --max-depth=2|sort|grep M
du: cannot access `./proc/18420/task/18420/fd/3': No such file or directory
du: cannot access `./proc/18420/task/18420/fdinfo/3': No such file or directory
du: cannot access `./proc/18420/fd/3': No such file or directory
du: cannot access `./proc/18420/fdinfo/3': No such file or directory
112M    ./usr/bin
11M     ./rofs/sbin
124M    ./lib
124M    ./rofs/lib
13M     ./boot
13M     ./lib/firmware
1.3M    ./lib/udev
14M     ./cdrom/pool
155M    ./var
1.8M    ./var/log
18M     ./var/tmp
2.0K    ./etc/NetworkManager
28M     ./usr/sbin
2.9M    ./rofs/boot
31M     ./home
31M     ./home/ubuntu
38M     ./var/cache
4.5M    ./etc/brltty
5.6M    ./bin
5.8M    ./rofs/bin
599M    ./usr/share
688M    ./cdrom/casper
7.0M    ./rofs/etc
735M    ./usr/lib
7.8M    ./etc
78M     ./rofs/var
95M     ./lib/modules
9.5M    ./sbin
98M     ./var/lib

```

deborphan doesn't free anything, cache files are clean.  any other ideas?

---

