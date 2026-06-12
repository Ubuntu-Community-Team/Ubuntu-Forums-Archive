---
title: "How i can install application on 2th HD? Need help please."
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by lurenzio on 2008-10-30
Hi, i have a mini notebook; the 1th hd is full, i need to install some applications in the 2th hd;
how i can install a deb package in a specific hd ?
is possible to add applications by sinaptic in a specific drive? Thanks

---

### Post by ddrichardson on 2008-10-31
I don't believe you can specify installation point, however you could mount the second drive as /opt and manually install files. This loses the functionality of apt-get in updating however.

dpkg-deb also allows you to extract the contents of a package.

---

