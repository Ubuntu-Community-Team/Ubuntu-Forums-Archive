---
title: "Boost package"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by maximp on 2007-11-14
Hi.
I'm using Ubuntu 7.04, and I need to install boost date-time package, e.g.
[(http://packages.ubuntu.com/gutsy/libs/libboost-date-time1.34.1)"][http://packages.ubuntu.com/gutsy/libs/libboost-date-time1.34.1](http://packages.ubuntu.com/gutsy/libs/libboost-date-time1.34.1)]("[http://packages.ubuntu.com/gutsy/libs/libboost-date-time1.34.1)

But unfortunately apt-get thinks there's no one:
$ sudo apt-get install libboost-date-time1.34.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libboost-date-time1.34.1

Why is that?
Thanks in advance.

---

### Post by taurus on 2007-11-14
But the link is for Gutsy!  What does your /etc/apt/sources.list look like anyway?

```
cat /etc/apt/sources.list
```

p.s.  Here's the package you want, [http://packages.ubuntu.com/feisty/libs/libboost-date-time1.33.1](http://packages.ubuntu.com/feisty/libs/libboost-date-time1.33.1).

---

### Post by maximp on 2007-11-15
Oh, thanks! I haven't paid attention to this, cause Boost 1.34.1 was released before GutsyGibbon.
Thank you again!

---

