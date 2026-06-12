---
title: "How to solve circular dependency in dpkg"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by worldy on 2008-05-24
g++-4.2_4.2.3-2ubuntu7_i386.deb depends on libstdc++6-4.2-dev
libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb depends on g++-4.2

what dpkg option must be given to install this two packages simultaneously

---

### Post by worldy on 2008-05-24
I got it 
dpkg -i file1.deb file2.deb

---

