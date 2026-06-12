---
title: "Building Modules Against Old Kernel Headers"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by ufalcon on 2006-10-14
This is a bit of a distro problem for me - I think I've narrowed down a GLX module issue to the fact that it's building against the 2.6.17-10-generic kernel, which will not work on my machine (neither will 2.6.17-9) - I'm using 2.6.17-7.  I've used Gentoo a fair bit, so I immediately tried creating a symlink:

```
/usr/src/linux -> /usr/src/linux-2.6.17-7-generic
```

which was suspiciously absent.  Not surprisingly, it didn't seem to do anything!

How do I get apt-get to build modules against the kernel I'm using?!  I've tried the following:

```
sudo apt-get install linux-restricted-modules-2.6.17-7-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-restricted-modules-2.6.17-7-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-restricted-modules-2.6.17-7-generic has no installation candidate

```

Hopefully this is an easy question!

---

### Post by ufalcon on 2006-10-14
Sorry!!!

Total n00b mistake folks, please disregard.  My problem was unrelated. I am somewhat perplexed that the binary package of a module linked to a newer kernel than what I'm running works for my current kernel... but I'll have to google that later.

---

