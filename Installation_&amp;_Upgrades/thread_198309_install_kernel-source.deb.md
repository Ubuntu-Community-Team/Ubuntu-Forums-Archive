---
title: "install kernel-source.deb"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by mfaridi on 2006-06-17
I downloaded kernel source and kenel image and kernel header for ubuntu 6 
they are deb package

Can I install them with this command 

sudo dpkg -i kernel*.deb

or I have to use 

apt-get install

---

### Post by x64Jimbo on 2006-06-17
You should probably install from the repositories. The reason being that the repositories in your sources.lst are configured just for your system, whether it's 32 bit or 64, or some other architecture, etc. It's a much better idea to install from the repos.

---

