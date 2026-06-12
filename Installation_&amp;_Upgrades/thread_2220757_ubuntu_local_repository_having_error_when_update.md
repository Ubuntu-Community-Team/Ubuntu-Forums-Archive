---
title: "ubuntu local repository having error when update"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by niraj_vara on 2014-04-29
Hi

  I have setup the ubuntu local repository for ubuntu updates. I have setup my local server on 192.168.1.63 by downloading around 63 GB data from ubuntu repository via  this command

apt-mirror /etc/apt/mirror.list 


when  I configure the local client and configure the sources.list for the local repostiry and runing 

apt-get update   --- getting the following error.

Err [http://192.168.1.63](http://192.168.1.63) precise/restricted Sources
  404  Not Found
Err [http://192.168.1.63](http://192.168.1.63) precise/universe Sources
  404  Not Found
Err [http://192.168.1.63](http://192.168.1.63) precise/multiverse Sources
  404  Not Found
Err [http://192.168.1.63](http://192.168.1.63) precise/main i386 Packages
  404  Not Found
Err [http://192.168.1.63](http://192.168.1.63) precise/restricted i386 Packages
  404  Not Found
Err [http://192.168.1.63](http://192.168.1.63) precise/universe i386 Packages
  404  Not Found
Err [http://192.168.1.63](http://192.168.1.63) precise/multiverse i386 Package

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/main/source/Sources](http://192.168.1.63/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/restricted/source/Sources](http://192.168.1.63/ubuntu/dists/precise/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/universe/source/Sources](http://192.168.1.63/ubuntu/dists/precise/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/multiverse/source/Sources](http://192.168.1.63/ubuntu/dists/precise/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/main/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/restricted/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/universe/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://192.168.1.63/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://192.168.1.63/ubuntu/dists/precise-updates/main/source/Sources](http://192.168.1.63/ubuntu/dists/precise-updates/main/source/Sources)  404  Not Found



Please guide how to solve this problem.

---

### Post by risk3715 on 2014-05-27
I'm having the same issue. I turned off my UFW to be sure it wasn't my firewall.

Here's my /etc/apt/sources.list
deb [http://192.168.1.x/ubuntu](http://192.168.1.x/ubuntu) trusty main restricted universe multiverse
deb [http://192.168.1.x/ubuntu](http://192.168.1.x/ubuntu) trusty-updates main restricted universe multiverse
deb [http://192.168.1.x/ubuntu](http://192.168.1.x/ubuntu) trusty-security main restricted universe multiverse

I installed apache2 and made a link from /var/www/ubuntu -> /[dest directory]/apt-mirror/mirror/archive.ubuntu.com/ubuntu

Here's my apt-mirror mirror.list contents:

set base_path /[dest directory]/apt-mirrorset nthreads     20
set _tilde 0

# trusty section
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-proposed main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted universe multiverse


# precise section
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse


clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

When I run apt-get update on client or even on the server (which has sources.list pointing to itself) I get:

Err [http://192.168.1.x](http://192.168.1.x) trusty/restricted Sources
404 Not Found
Err [http://192.168.1.x](http://192.168.1.x) trusty/universe Sources
404 Not Found
Err [http://192.168.1.x](http://192.168.1.x) trusty/multiverse Sources
404 Not Found
Err [http://192.168.1.x](http://192.168.1.x) trusty/main i386 Packages
404 Not Found
Err [http://192.168.1.x](http://192.168.1.x) trusty/restricted i386 Packages
404 Not Found
Err [http://192.168.1.x](http://192.168.1.x) trusty/universe i386 Packages
404 Not Found
Err [http://192.168.1.x](http://192.168.1.x) trusty/multiverse i386 Package

... .... etc

What am I doing wrong?

---

