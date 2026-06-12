---
title: "open ssh wont install"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by endoglastic on 2012-01-11
I've been trying to install open ssh, and it just wont get it, here's what it says in the terminal


sam@sam-desktop:~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate



if you can help me, i would appreciate it. Using 9.10 edition of ubuntu.

---

### Post by endoglastic on 2012-01-11
i actually cant even get updates....

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by hansdown on 2012-01-11
Hi, endoglastic.

9.10 reached end of life in april 2011.

The repositories are closed.

---

