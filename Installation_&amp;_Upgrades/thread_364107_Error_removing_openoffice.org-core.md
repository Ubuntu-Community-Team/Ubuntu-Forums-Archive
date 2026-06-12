---
title: "Error removing openoffice.org-core"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by LinuxMike on 2007-02-17
I am new to linux and a new Ubuntu user.  I recently followed the excellent directions posted to upgrade OpenOffice 2.04 to 2.1.  However, I tried to remove the openoffice.org-core so I could installed the openoffice.org-debian-menus_2.1-5_all.deb.  However when I try to remove the file via Snaptic Package Manager I get the following error: "Couldn't apply changes! Fix broken packages first."  Any help in solving this issue would be greatly appreciated.  Thanks.

---

### Post by K.Mandla on 2007-02-18
Double-check the [man pages for apt-get]("http://www.die.net/doc/linux/man/man8/apt-get.8.html") before you try it, but I believe 

```
sudo apt-get -f _________
```

will force your system to try and correct some of the offending packages.

---

