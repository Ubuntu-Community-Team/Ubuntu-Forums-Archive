---
title: "3 not upgraded - ubuntu 18.04.6 LTS 32 bit"
date: 2022-07-19
forum: Installation &amp; Upgrades
---

### Post by Krischu on 2022-07-19
Since some point in time already  my manual upgrade which I'm doing as

apt-get update
apt-get upgrade

leave 3 packages not updated, so everytime I'm rebooting I'm told when logging in :

8 updates can be applied immediately.
8 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

apt list --upgradable
Listing... Done
linux-generic/bionic-updates,bionic-security 4.15.0.189.174 i386 [upgradable from: 4.15.0.169.158]
linux-headers-generic/bionic-updates,bionic-security 4.15.0.189.174 i386 [upgradable from: 4.15.0.169.158]
linux-image-generic/bionic-updates,bionic-security 4.15.0.189.174 i386 [upgradable from: 4.15.0.169.158]

What's impeding this process?

---

### Post by Impavidus on 2022-07-19
Upgrading those packages requires installation of some new packages. [s]apt upgrade[/s] apt-get upgrade never installs new packages to satisfy dependencies, so it doesn't upgrade those packages. Use```
apt-get dist-upgrade
```or```
apt upgrade
```instead, both as root (obviously).

It has been like that forever, so I'm a bit puzzled on what may have caused your issue now.

---

### Post by Krischu on 2022-07-20
> **Impavidus said:**
> Upgrading those packages requires installation of some new packages. apt upgrade never installs new packages to satisfy dependencies, so it doesn't upgrade those packages. Use```
apt-get dist-upgrade
```or```
apt upgrade
```instead, both as root (obviously).

It has been like that forever, so I'm a bit puzzled on what may have caused your issue now.

You write: " apt upgrade never installs new packages to satisfy dependencies, so it doesn't upgrade those packages. ..." Then later you recommend "apt upgrade"?

Assuming that was a typo and you meant "apt-get upgrade" in the first place.

I did the "apt-get dist-upgrade" and the number of packages to upgrade was 0 after that.

Before:

Welcome to Ubuntu 18.04.6 LTS (GNU/Linux 4.15.0-169-generic i686)

Now:

Welcome to Ubuntu 18.04.6 LTS (GNU/Linux 4.15.0-189-generic i686)

---

### Post by rsteinmetz70112 on 2022-07-20
Apt is a newer utility that mostly does what apt-get does but offers slightly different commands as well as combining the functions of some other utilities. It is somewhat more user friendly. The old **apt-get upgrade** command updates all the packages which currently exist in your system. It does not install or remove the existing package on your system. However, the newer **apt upgrade** command installs packages that were added as dependencies of upgradable packages.

It is now generally recommended that users use **apt update** and **apt upgrade** instead of the apt-get versions.

---

### Post by Impavidus on 2022-07-20
> **Krischu said:**
> 
Assuming that was a typo and you meant "apt-get upgrade" in the first place.

Yes, it was a typo. I fixed it.

---

