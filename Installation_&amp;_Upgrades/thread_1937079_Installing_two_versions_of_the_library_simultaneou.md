---
title: "Installing two versions of the library simultaneously"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by arttykh on 2012-03-07
**What I have:** Ubuntu 10.10, libexpat library version 2.0.1.
**What I need:** Install the libexpat library version 2.0.0.
**What I do**: download from [http://expat.sourceforge.net/](http://expat.sourceforge.net/) source for libexpat-2.0.0. Make. Install. By default, placed in / usr / local / lib:

```
$ / usr / local / lib /
libexpat.a libexpat.la libexpat.so libexpat.so.1 libexpat.so.1.5.0
```

But the list of installed libraries does not have this version:

```
$ / sbin / ldconfig-p | grep libexpat
  libexpatw.so.1 (libc6) => / lib/libexpatw.so.1
  libexpat.so.1 (libc6) => / lib/libexpat.so.1
```

```
$ dpkg-l | grep 'ii libexpat'
ii libexpat1 2.0.1-7ubuntu1
```

**Question:** How to make  libexpat-2.0.0 available for applications?

**The global question is:** Does Ubuntu have a mechanism of simultaneous installation of different versions of the library?

Thanks in advance!

---

