---
title: "Clean install and update problem"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by xalaros on 2008-02-01
Hello i am a problem after clean installation of ubuntu gutsy 7.10. Although installation was fine i did the automatic package update once i logged in. after that i always get the following errors when i try to install any packages.

E: ttf-opensymbol: subprocess post-installation script returned error exit status 49
E: openoffice.org-core: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured

The packages i try to install seem to work fine after installation. Can you please help with this problem

---

### Post by PmDematagoda on 2008-02-01
Post the outputs of:-
```
sudo dpkg --configure -a
```

Also, post the output of:-
```
cat /etc/apt/sources.list
```

---

