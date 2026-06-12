---
title: "Seg fault when updating"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by snaga on 2006-09-26
I'm trying to do an update this morning, and I'm getting a seg fault. Here's what I'm seeing:

```

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-headers-686 linux-image-686 linux-restricted-modules-686
The following packages will be upgraded:
  firefox libgnutls12 libnspr4 libnss3 linux-686 linux-headers-2.6.15-26 linux-headers-2.6.15-26-686 linux-image-2.6.15-26-686 linux-restricted-modules-2.6.15-26-686
  linux-restricted-modules-common mozilla-thunderbird nvidia-glx
12 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/61.7MB of archives.
After unpacking 168kB of additional disk space will be used.
Do you want to continue [Y/n]? y
/bin/sh: line 1:  5924 Segmentation fault      /usr/sbin/dpkg-preconfigure --apt
Setting up gzip (1.3.5-12ubuntu0.1) ...
/var/lib/dpkg/info/gzip.postinst: line 6:  5927 Segmentation fault      install-info --quiet --section "\QUtilities\E" "Utilities" /usr/share/info/gzip.info
dpkg: error processing gzip (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 gzip
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Its probably been a couple of weeks since I updated. I tried an apt-get clean, which did no good. Here's my sources.lst:

```

deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

```

This seems to happen if I do a full upgrade, or if I try to upgrade just one package, like firefox. I'm grateful for any ideas.

---

