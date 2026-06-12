---
title: "Install a Debian Wheezy package into Ubuntu"
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by kevpatts2 on 2014-08-29
Hey,

Have an old system running 10.04. I've been told that the mod-security package is too old and I need to update to this version: [https://packages.debian.org/search?searchon=sourcenames&keywords=modsecurity-apache](https://packages.debian.org/search?searchon=sourcenames&keywords=modsecurity-apache)

Can you install debian packages in ubuntu? I've tried doenloading the package and using dpkg -i but there are dependancy problems. I then tried adding the deb line into sources.list but had keyring signature issues even after installing the "debian-keyring" package from ubuntu repos.

Thanks in advance,
Kev

---

### Post by uRock on 2014-08-29
Right-click and open the .deb with Ubuntu Software Center, which will install the dependancies is they are in the repos.

You can also install the dependencies listed in the terminal using apt-get, then run **sudo apt-get install -f**

---

