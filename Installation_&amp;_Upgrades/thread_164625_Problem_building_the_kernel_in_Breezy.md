---
title: "Problem building the kernel in Breezy"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by josemanuel on 2006-04-23
Hello all. I am trying to install a webcam Logitech Notebook model on my laptop with ubuntu breezy 5.10. (kernel 2.6.12-10-386). I closely follow the instructions of the Wiki How To, namely I do:

$ sudo apt-get install build-essential
$ mkdir ~/linux
$ cd ~/linux
$ apt-get source linux-source-2.6.12
$ cd linux-source-2.6.12-2.6.12

 And enable only my architecture:

$ cd  config/i386
$ mkdir disabled
$ mv * disabled
$ mv disabled/686 .

The problem is that when I  do :

$ cd ~/linux/linux-source-2.6.12-2.6.12
$ dpkg-buildpackage -B -uc -us -rfakeroot

I get: 

dpkg-buildpackage: source package is linux-source-2.6.12
dpkg-buildpackage: source version is 2.6.12-10.30
dpkg-buildpackage: source changed by Ben Collins <bcollins@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: xmlto docbook-utils kernel-package (>= 9.001ubuntu5) sharutils transfig dpatch kernel-wedge (>= 2.05ubuntu3) gcc-3.4 (>= 3.4.4-0ubuntu6)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)


 As I had very bad experiences in the past with the dependencies (and forcing unsatisfied ones...) I am afraid  to do "override". 

Some hints of what can I do?.

---

