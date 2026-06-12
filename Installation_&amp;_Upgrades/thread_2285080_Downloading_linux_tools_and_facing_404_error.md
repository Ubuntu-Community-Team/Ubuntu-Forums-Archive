---
title: "Downloading linux tools and facing 404 error"
date: 2015-07-03
forum: Installation &amp; Upgrades
---

### Post by rohit19 on 2015-07-03
*_**HI i am trying to install the linux tools using the command :**_*

sudo apt-get install linux-tools


_***But I am getting the following error:***_





WARNING: The following packages cannot be authenticated!
  libdw1 linux-tools-common linux-tools-3.11.0-26 linux-tools-3.11.0-26-generic linux-tools-generic
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) saucy-updates/main libdw1 i386 0.157-1ubuntu1.1
  404  Not Found [IP: 91.189.92.201 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main libdw1 i386 0.157-1ubuntu1.1
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main linux-tools-common all 3.11.0-26.45
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main linux-tools-3.11.0-26 i386 3.11.0-26.45
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main linux-tools-3.11.0-26-generic i386 3.11.0-26.45
  404  Not Found [IP: 91.189.91.15 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main linux-tools-generic i386 3.11.0.26.27
  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/elfutils/libdw1_0.157-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/elfutils/libdw1_0.157-1ubuntu1.1_i386.deb)  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-tools-common_3.11.0-26.45_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-tools-common_3.11.0-26.45_all.deb)  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-tools-3.11.0-26_3.11.0-26.45_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-tools-3.11.0-26_3.11.0-26.45_i386.deb)  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-tools-3.11.0-26-generic_3.11.0-26.45_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-tools-3.11.0-26-generic_3.11.0-26.45_i386.deb)  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-tools-generic_3.11.0.26.27_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-tools-generic_3.11.0.26.27_i386.deb)  404  Not Found [IP: 91.189.91.15 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[U][I][B]
Please help me resolve this issue.[/B][/I][/U]

---

### Post by deadflowr on 2015-07-03
Saucy is dead.
Therefor so are the repositories for it.
You need to install a fresh supported version.
(Or rather not needed, but it is the easiest safest way to go, IMHO)
Ubuntu 14.04, which is one version up from saucy, is an LTS (long term support) version.
I suggest going with that one.

---

