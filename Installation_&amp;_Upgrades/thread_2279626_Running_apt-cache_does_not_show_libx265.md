---
title: "Running apt-cache does not show libx265"
date: 2015-05-24
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2015-05-24
Folks,

Environment: Ubuntu 14.04.2 LTS

When I searched for libx265 package on the Internet, I found one at [http://packages.ubuntu.com/vivid/libx265-43](http://packages.ubuntu.com/vivid/libx265-43). The description indicates that the package is available in the universe repository.

I checked my sources.list and "universe" repository is indeed present:

```
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

```

However, when I search for libx265, I don't find any package at all:

```
$ sudo apt-get update
$ apt-cache search libx265

```

Can someone please tell me what is it that I am missing?

Regards,
Peter

---

### Post by monkeybrain20122 on 2015-05-24
Your link is for vivid but you are apparently running trusty from your sources list.

x265 is not in Trusty or Utopic but in vivid 

[https://launchpad.net/ubuntu/+source/x265](https://launchpad.net/ubuntu/+source/x265)

For trusty you have to get it from a ppa, e.g [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by PeterTaps on 2015-05-25
Oh. Missed a finer detail:-(.

Thank you for your help.

Peter

---

