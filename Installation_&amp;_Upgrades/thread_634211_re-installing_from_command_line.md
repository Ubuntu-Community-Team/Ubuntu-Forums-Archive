---
title: "re-installing from command line"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by areks on 2007-12-07
Hi,

I was installing Ubuntu 7.10 on my older laptop today (before I head Win + Ubuntu 6.10). Formating and installing kernel worked fine. Unfortunately I was not able to finish installing software packages probably because CD drive failed during this process. I'm also not able to boot from CD any more.

As far I can see I have working Linux kernel, and I can login into command line.
Does anybody knows how to re-install Ubuntu from command line, or install graphic system with apt-get. I would like to install standard Gnome version of Ubuntu.

Thanks in advance.

---

### Post by taurus on 2007-12-07
```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

