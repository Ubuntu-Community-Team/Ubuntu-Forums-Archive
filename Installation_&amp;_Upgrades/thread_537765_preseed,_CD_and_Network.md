---
title: "preseed, CD and Network"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by gehel on 2007-08-29
I'm playing around with preseeds. It works mostly well, except :

I'd like to be able to automagically download and install a couple of packages, especially xemacs21. I added the following lines to my preseed :

d-i mirror/country string enter information manually
d-i mirror/http/hostname string mirror.switch.ch
d-i mirror/http/directory string /ftp/mirror/ubuntu
d-i mirror/http/proxy string
d-i mirror/suite string feisty
d-i mirror/udeb/suite string feisty

d-i pkgsel/include string xemacs21

The install fails by not being able to download the package. I know that I could include the package on the CD, but I'd like to be able to access any package in the Ubuntu repository. I'm a bit lost, and cant find the right docs. Any pointer ?

---

