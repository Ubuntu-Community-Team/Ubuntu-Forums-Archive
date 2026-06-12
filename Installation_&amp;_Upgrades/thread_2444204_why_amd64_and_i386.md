---
title: "why amd64 and i386?"
date: 2020-05-26
forum: Installation &amp; Upgrades
---

### Post by martin30002 on 2020-05-26
I have one machine with ubuntu 20.04 where all packages are installed as both amd64 and i386. On another machine only amd64 packages are installed.
Can I get rid of the i386 packages?

---

### Post by deadflowr on 2020-05-26
> all packages are installed as both amd64 and i386
They aren't. Only a handful ( a large handful) of packages have been built for 32-bit.

It means you have the system configured to use i386 packages, meaning something you use requires 32-bit packages.
(Wine is a common package set that still requires 32-bit, for example)

See here for a breakdown of what's what in regards to 32-bit on 20.04 as well as a list of 32-bit packages built for it:
[https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598]("https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598")

---

