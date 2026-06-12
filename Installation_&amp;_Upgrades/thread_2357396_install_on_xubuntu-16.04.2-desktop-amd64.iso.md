---
title: "install on xubuntu-16.04.2-desktop-amd64.iso"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by jgarry on 2017-04-01
trying to install
gcc_6.1.1-1ubuntu2_amd64.deb
which says I need 
g++_6.1.1-1ubuntu2_amd64.deb
but this says I need the first deb file.

gcc -v says no version of gcc is installed. 

How do I do this? I'm obviously on the wrong track.

---

### Post by oldos2er on 2017-04-01
Looks like you can use this PPA to install gcc6 on Xenial: [https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test?field.series_filter=xenial](https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test?field.series_filter=xenial)
Disclaimer: I've not tried this myself.

---

