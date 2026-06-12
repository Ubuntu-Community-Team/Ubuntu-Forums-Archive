---
title: "x11 deb pkg circular reference?"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by sunfisher on 2006-12-12
I'm trying to install two deb packages and each one lists the other as a dependency. How do I get around this? The packages are:
libx11-dev_1.0.3-0ubuntu4_i386.deb 
libxext-dev_1.0.1-1ubuntu1_i386.deb

This occurs on Xubuntu, Kubuntu and Ubuntu 6.10.
](*,) :confused:

---

### Post by mcduck on 2006-12-12
you can install both at the same time from command line with 'sudo dpkg -i libx11-dev_1.0.3-0ubuntu4_i386.deb libxext-dev_1.0.1-1ubuntu1_i386.deb'

---

### Post by sunfisher on 2006-12-12
Worked like a charm, firtst time. Thanks, :)

---

