---
title: "unable to install packages on ubuntu 12.04"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by khoshalar on 2013-05-16
Hi,

i am trying configure an app server on Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic x86_64),i am logged in as root, and when I run apt-get install apache2 , apt-get update and apt-get upgrade .,I get these following errors.,

Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates/main openssl amd64 1.0.1-4ubuntu5.9
  403  Forbidden [IP: 91.189.91.15 80]

.........................................

Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13.1_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools-bin_0.99ubuntu13.1_amd64.deb)  403  Forbidden [IP: 91.189.91.15 80]
....................................................
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I also tried apt-get install --fix-missing

I am unable to install any packages., please suggest.,

thanks in advance.

---

### Post by linuxtechguy on 2013-05-17
You need to pick a different mirror to get your files from and update /etc/apt/sources.list

---

