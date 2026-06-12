---
title: "to convert java binary package to debian package"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by project on 2008-02-09
i downloaded a java.bin package......
and have been trying to convert these java.bin package to .deb package
but unable to do so..........i tried using fakeroot make-dpkg........so i can get the solution

---

### Post by zvacet on 2008-02-09
System<admin>software sources<chek all boxes under ubuntu and updates tab.Reload.in programs>accessories>terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

**for KDE **

```
sudo apt-get install kubuntu-restricted-extras
```

**for Xubuntu **

```
sudo apt-get install xubuntu-restricted-extras
```

Run one of these commands(depends wich DE you use)and you will get Java,flash,plugins.....

---

