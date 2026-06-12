---
title: "kernel panic"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by ktroxe on 2006-07-18
Hi.

I`m trying to install ubuntu server in a very old PC, and after few seconds of have chosen the installatoin mode (normal, LAMP...) I take the following problem:

[100.735688] <0> Kernel panic - not syncing: Attemped to kill init!

The PC is a P 133MHz with 16 MB of RAM.

Thank you.

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **ktroxe said:**
> Hi.

I`m trying to install ubuntu server in a very old PC, and after few seconds of have chosen the installatoin mode (normal, LAMP...) I take the following problem:

[100.735688] <0> Kernel panic - not syncing: Attemped to kill init!

The PC is a P 133MHz with 16 MB of RAM.

Thank you.

I don't believe that that computer can run a normal linux kernel. Maybe UcLinux would be a better option. It's basically a stripped-down kernel that can run better on old machines. Plus I don't think much of your hardware would be supported since the 2.6 kernel series "dumps" support for very old machines.

---

