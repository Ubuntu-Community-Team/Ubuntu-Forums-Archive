---
title: "ubuntu 20.04 can't be upgraded"
date: 2020-04-18
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2020-04-18
Hi
How to deal with the issues bellow ?

sudo apt list --upgradable 
Listing... Done
linux-image-generic/focal-proposed 5.4.0.25.31 amd64 [upgradable from: 5.4.0.24.30]
N: There is 1 additional version. Please use the '-a' switch to see it
test01@test01:~$ sudo apt list --upgradable  -a
Listing... Done
linux-image-generic/focal-proposed 5.4.0.25.31 amd64 [upgradable from: 5.4.0.24.30]
linux-image-generic/focal,focal,now 5.4.0.24.30 amd64 [installed,upgradable to: 5.4.0.25.31]


Cheers

---

### Post by sudodus on 2020-04-18
What happens when you try upgrading with the following command line?

```

sudo apt full-upgrade

```

Edit: I  tried in my current Lubuntu Focal and it upgraded to kernel version 5.4.0.24.30 (not ...31).

---

### Post by CatKiller on 2020-04-18
> **hoboy said:**
> linux-image-generic/focal-**proposed** 5.4.0.25.31 amd64 [upgradable from: 5.4.0.24.30]

Packages in the [Proposed](https://wiki.ubuntu.com/Testing/EnableProposed) repository haven't been released. They are there for specific testing.

---

### Post by hoboy on 2020-04-18
sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
test01@test01:~$ sudo apt list --upgradable -a
Listing... Done
linux-image-generic/focal-proposed 5.4.0.25.31 amd64 [upgradable from: 5.4.0.24.30]
linux-image-generic/focal,focal,now 5.4.0.24.30 amd64 [installed,upgradable to: 5.4.0.25.31]

hasn't help
Tks

---

### Post by sudodus on 2020-04-18
I think your system is not ready yet for kernel 5.4.0.25.31, or to put it the other way around: kernel 5.4.0.25.31 is not ready yet for your system.

---

### Post by hoboy on 2020-04-18
Tks

---

