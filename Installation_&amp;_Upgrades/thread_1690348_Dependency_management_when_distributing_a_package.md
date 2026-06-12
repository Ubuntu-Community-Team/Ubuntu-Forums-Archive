---
title: "Dependency management when distributing a package"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by gabipetrovay on 2011-02-18
Hi,

I am distributing a package that depends on libgvc. The package is built on a Ubuntu 10.04. In this distribution libgvc is available as: /usr/lib/libgvc.so.4.0.0

**Q1**: how can I find which package brought this? (I assume it's graphviz but I want to check this)

Now when I install this package on another Ubuntu 10.04 everything works ok and the required dependency on graphvis is installed.

But when I install it on a 10.10 I get the following problem:
**libgvc.so.4: cannot open shared object file: No such file or directory**
This is because 10.10 can only install libgvc.so.5

**Q2**: How can I manually install old versions of packages on newer distributions? (with apt-get or Synaptic Package Manager)

**Q3**: Are there any general solution for distributing one package for different distributions (10.04 and 10.10 in this case) or should I create one package for each?

Thnks!
Gabriel

---

