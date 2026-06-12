---
title: "Packages broken on Install CD"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by ljdellar on 2005-11-25
I installed from the latest CD (Yesterday) and got a warning during the installation phase that some packages were broken and that I needed to use Synaptic when I finished installing to fix them.

I tried using Synaptic, but I keep getting a failure at:

E: /var/cache/apt/archives/libperl5.8_5.8.7-5ubuntu1_i386.deb: subprocess dpkg-deb --control returned error exit status 2

Anyone know what this means?

Thanks if you can help

LJdellar:confused:

---

### Post by Xian on 2005-11-25
What is the output of this terminal command?:

```
$ sudo apt-get -f install
```

---

