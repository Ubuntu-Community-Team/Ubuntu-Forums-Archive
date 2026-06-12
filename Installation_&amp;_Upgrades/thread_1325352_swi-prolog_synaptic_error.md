---
title: "swi-prolog synaptic error"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by akoskm on 2009-11-13
Hi!
I'm trying to install the swi-prolog package from synaptic package manager, but it gives me an error after marking it for installation - and accepting the list off additional packages.
```

swi-prolog:
 Depends: libgmp3-dev but it is not going to be installed
 Depends: libreadline5-dev but it is not going to be installed

```.
What is the problem?
Any ideas? Thank you.

---

### Post by akoskm on 2009-11-15
After some searching I've figured out that the swi-prolog have unsatisfied dependency with the package:

1. libncurses5-dev
2. libncurses5-dev with libncurses5
3. libncurses5 with 1.

The point is that booth packages are contained in Synaptic so why??
After searching the Ubuntu package repositories I found the same package here:
[http://packages.ubuntu.com/karmic/i386/libncurses5-dev/download]("http://packages.ubuntu.com/karmic/i386/libncurses5-dev/download")
...so I've added:
deb [http://cz.archive.ubuntu.com/ubuntu]("http://cz.archive.ubuntu.com/ubuntu") karmic main 
to the sources.list and now everything installs fine.

---

