---
title: "Can not install software"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by Pushpalanka on 2011-04-05
When I try to install any program this kind of error comes. I can not even open Software Center,:confused: 10:10version is used.

[B]root@pushpalanka-Latitude-D830:/home/pushpalanka# apt-get install vim
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/B]

---

### Post by mörgæs on 2011-04-05
Try to boot the machine and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Pushpalanka on 2011-04-07
Thanx a lot. It resolved the problem. :)

---

### Post by garvinrick4 on 2011-04-07
Mark your thread as solved in upper left thread tools please.

---

