---
title: "How to install g++ compiler packages on ubuntu 10.04"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by alber1 on 2010-06-30
I'm not connected to the web at this time.

---

### Post by sgosnell on 2010-06-30
You'll need to get the .deb package for build-essential somehow, then copy to the non-connected computer and run dpkg on it, or use gdebi to do the install.  You can do this by using another Ubuntu computer that is connected, and use the -d option with apt-get.  That just downloads the packages without unpacking or installing them.  They'll be in /var/cache/apt/archives/, and you can copy everything there to the unconnected computer, just to make sure you got everything.

---

