---
title: "Upgrading from 5.10 without desktop"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by JCorrea920 on 2006-06-09
Is it possible to upgrade without Ubuntu-desktop installed I am currently using fluxbox? Would like to upgrade several servers.
There is one server that has desktop installed but it also has fluxbox and VMWare with W2K3 Enterprise Server on the iron. I want to upgrade but cannot afford to render a production server useless. Should I just follow the upgrade directions on the WIKI for Dapper or what?:confused:

---

### Post by aysiu on 2006-06-09
Yeah, just change your /etc/apt/sources.list and do a find/replace on the word *breezy* for the word *dapper* and ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

