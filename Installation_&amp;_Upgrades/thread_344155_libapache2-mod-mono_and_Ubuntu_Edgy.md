---
title: "libapache2-mod-mono and Ubuntu Edgy"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by veza on 2007-01-22
Hey guys.

I try get Mod_mono work with Apache2 under Ubuntu Edgy. but seems like edgy doesn't have package name "libapache2-mod-mono" ( ? ) I get this error: 

[COLOR="Sienna"]"The following packages have unmet dependencies:
libapache2-mod-mono: Depends: mono-apache-server (< 1.1.14) but it is not going to be installed or mono-apache-server2 (< 1.1.14) but 1.1.17.1-2 is to be installed"[/COLOR]


The installation tutorial i'm following is [https://help.ubuntu.com/community/ModMono]("https://help.ubuntu.com/community/ModMono")

---

### Post by c-2501 on 2007-01-31
im having this problem too on a brand new install, ive seen the bug reported elsewhere but no workaround for it yet.

if anyone knows a way to fix it that'd be great

---

### Post by byjg on 2007-03-07
Hi, I run the follow work-around to solve this problem:

1) Download and build .deb package from Source Repository:

```
sudo apt-get source --build libapache2-mod-mono
```

2) Install the package

```
sudo apt-get install mono-apache-server
sudo dpkg -i libapache2-mod-mono_1.1.17-3_amd64.deb
```

I hope this help anyone.

---

