---
title: "installing software packages from debian dvd"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by -@23%^yu* on 2013-12-23
is there a way to add a debian dvd to install software packages in ubuntu 13.10

---

### Post by fantab on 2013-12-24
It may be possible since both Debian and Ubuntu use '.deb' format to install packages. However it is NOT recommended that you do so.
If you need to install any software install those ONLY from the Ubuntu Repositories.

By the way, what 'software packages' are you trying to or want to install?

---

### Post by -@23%^yu* on 2013-12-24
> **fantab said:**
> It may be possible since both Debian and Ubuntu use '.deb' format to install packages. However it is NOT recommended that you do so.
If you need to install any software install those ONLY from the Ubuntu Repositories.

By the way, what 'software packages' are you trying to or want to install?
Irrespective of the packages to be installed i just wanted to know the method to add debian dvd as a repo to install wine. Though i know that wine can be installed through app store.

---

### Post by ian-weisser on 2013-12-24
WARNING: You can break your system by mixing packages from different versions of Ubuntu and/or Debian. Binary packages from different versions are compiled against different toolchains, and may be incompatible. If you override your package manager to install incompatible archives/repositories, you may **break your package manager**, install packages that **break your system beyond recovery**, and **lose data**.

The answer to your question is to add the Debian archive to /etc/apt/sources.list or /etc/apt/sources.list.d/

---

### Post by -@23%^yu* on 2013-12-25
thankyou. Better to stay away from installing from debian cd.

---

