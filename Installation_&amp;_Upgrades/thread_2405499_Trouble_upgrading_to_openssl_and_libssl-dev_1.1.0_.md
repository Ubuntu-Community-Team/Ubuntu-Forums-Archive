---
title: "Trouble upgrading to openssl and libssl-dev 1.1.0 on Ubuntu 14.04"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by ecolaneadam on 2018-11-06
A couple of months ago I was upgrading openssl with the following versions via apt:
        - libssl-dev=1.1.0h-2.0+ubuntu14.04.1+deb.sury.org+1
        - openssl=1.1.0h-2.0+ubuntu14.04.1+deb.sury.org+1

but when I ran a deployment again yesterday, I am getting back that it is failing to find the version.

Any recommendations on what the proper version to be used?

---

### Post by deadflowr on 2018-11-06
The openssl packages you want aren't in the regular archives but from this ppa:
[https://launchpad.net/~ondrej/+archive/ubuntu/php/+index?batch=75]("https://launchpad.net/~ondrej/+archive/ubuntu/php/+index?batch=75")
You'll need to follow the directions to add the ppa if you want to add the ppa.

---

