---
title: "Problem installing build-deps for vlc"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by garyvdm on 2007-12-19
Hi

When i run
```
$ sudo apt-get build-dep vlc
```
I get
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for vlc could not be satisfied.

```

This is my  /etc/apt/sources.list
```
deb http://za.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse

deb http://za.archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted

deb http://za.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted

deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted

```

Someone had the same problem, but came right. (see [this thread]("http://ubuntuforums.org/showthread.php?t=516003&page=2").) But that was festy. has something changed in gutsy, or am I doing somthing wrong?

Gary

---

### Post by santaslittlehelper on 2007-12-20
Hi, it works fine here, have a look at "System > Administration > Software Sources".
Maybe you need to add Medibuntu to you're sources.
[https://help.ubuntu.com/community/RestrictedFormats#w32codecs](https://help.ubuntu.com/community/RestrictedFormats#w32codecs)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I guess there's a reason too why you what to build vlc so I wont ask. :)

---

### Post by garyvdm on 2007-12-20
Thank you santaslittlehelper. I worked when I added Medibunut to my source.list.

I want to build vlc because I want to use the [vlc python bindings]("http://wiki.videolan.org/Python_bindings"), and it seams that at the moment, if you want them, you need to build them.

Gary

---

