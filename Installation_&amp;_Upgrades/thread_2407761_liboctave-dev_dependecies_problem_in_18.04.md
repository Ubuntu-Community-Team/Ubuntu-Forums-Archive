---
title: "liboctave-dev dependecies problem in 18.04"
date: 2018-12-08
forum: Installation &amp; Upgrades
---

### Post by k.s.v. on 2018-12-08
I am trying to install liboctave-dev on Ubuntu 18.04. Tracing the unmet dependencies located the problems (I omit intermediate steps):

Depends: libtinfo5 (= 6.1-1ubuntu1) but 6.1-1ubuntu1.18.04 is to be installed
Depends: libncurses5 (= 6.1-1ubuntu1) but 6.1-1ubuntu1.18.04 is to be installed
Depends: libjpeg-turbo8 (= 1.5.2-0ubuntu5) but 1.5.2-0ubuntu5.18.04.1 is to be installed

I can not downgrade (force version) for these packages because in order to do that I was asked to remove a considerable list of packages and applications, which I use. 

Is there a way to resolve this situation?

---

