---
title: "Can I install specific iso files for Lubuntu onto Ubuntu 9.10 to get internet?"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by haplorrhine on 2012-07-26
I could only successfully install Ubuntu 9.10 onto my laptop, but it doesn't detect wireless signals. I have a flashdrive with the iso files for the latest 32bit Lubuntu. Running Lubuntu on the laptop from the flashdrive, it detects wireless signals, but it freezes when I try to connect. No ethernet cable, I'm at a library.

---

### Post by dino99 on 2012-07-26
sorry dupe, see below

---

### Post by dino99 on 2012-07-26
the main difference is that ubuntu use gnome while Lubuntu use lxde.

but i think you might install the latest kernel (3.5) for better driver support. You can install this ppa:

ubuntu-x-swat/q-lts-backport from launchpad

[https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport)

otherwise, to get around installation, you might need to add some boot option (google around "ubuntu boot option") like nomodeset or noacpi.

---

### Post by haplorrhine on 2012-07-26
Thanks for your help. :)
Due to the information you gave me, I am trying a different solution to my problem.

---

