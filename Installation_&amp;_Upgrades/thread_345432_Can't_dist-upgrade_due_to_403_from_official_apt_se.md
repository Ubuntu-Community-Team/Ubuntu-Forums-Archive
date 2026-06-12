---
title: "Can't dist-upgrade due to 403 from official apt servers"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by lozenge on 2007-01-24
```
james@monkey:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
*PACKAGES*
1050 upgraded, 211 newly installed, 60 to remove and 34 not upgraded.
Need to get 15.0MB/867MB of archives.
After unpacking 460MB of additional disk space will be used.
Do you want to continue [Y/n]?
Err http://archive.ubuntu.com edgy-updates/main libc6-pic 2.4-1ubuntu12.2
  403 Forbidden [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-updates/main libc6-prof 2.4-1ubuntu12.2
  403 Forbidden [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-updates/main libc6-dev 2.4-1ubuntu12.2
  403 Forbidden [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-updates/main libc6-dbg 2.4-1ubuntu12.2
  403 Forbidden [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-updates/main libc6 2.4-1ubuntu12.2
  403 Forbidden [IP: 195.248.90.35 80]
Err http://archive.ubuntu.com edgy-updates/main libc6-i686 2.4-1ubuntu12.2
  403 Forbidden [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-pic_2.4-1ubuntu12.2_i386.deb  403 Forbidden [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-prof_2.4-1ubuntu12.2_i386.deb  403 Forbidden [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb  403 Forbidden [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.4-1ubuntu12.2_i386.deb  403 Forbidden [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.4-1ubuntu12.2_i386.deb  403 Forbidden [IP: 195.248.90.35 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.4-1ubuntu12.2_i386.deb  403 Forbidden [IP: 195.248.90.35 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

ANY clue? I don't.

---

### Post by evilghost on 2007-01-24
Try using us.archive.ubuntu.com

---

