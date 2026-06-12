---
title: "kparted installation problem"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by tomsturge on 2007-02-17
While trying to install Kparted in Kubuntu i got to './configure' stage and when it ran the command it was stopped with the following message:

checking whether the C++ compiler (gcc   ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.

Ive also tried installing Qtparted without success, but not at the same point.

---

### Post by aysiu on 2007-02-17
Any reason you're compiling from source?

Do this instead: ```
sudo aptitude update
sudo aptitude install qtparted
kdesu qtparted
``` or, if you're using Ubuntu (instead of Kubuntu), do this: ```
sudo aptitude update
sudo aptitude install gparted
gksudo gparted
``` Then read:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

