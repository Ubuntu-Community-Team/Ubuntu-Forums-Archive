---
title: "Updating from Default install causes OpenOffice Errors"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by Leebobs on 2007-09-02
I have done a default install using the Ubuntu 7.04 Alternative CD and have updated using the default repositories and using the update manager and I get the following error:

> E: ttf-opensymbol: subprocess post-installation script returned error exit status 58
E: openoffice.org-core: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-filter-mobiledev: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured

I tried to re-install the Openoffice.org-core package and the error seems to relate to ttf-opensymbol.

> E: ttf-opensymbol: subprocess post-installation script returned error exit status 33
E: openoffice.org-core: dependency problems - leaving unconfigured
E: python-uno: dependency problems - leaving unconfigured
E: openoffice.org-writer: dependency problems - leaving unconfigured
E: openoffice.org-calc: dependency problems - leaving unconfigured
E: openoffice.org-draw: dependency problems - leaving unconfigured
E: openoffice.org-impress: dependency problems - leaving unconfigured
E: openoffice.org-math: dependency problems - leaving unconfigured
E: openoffice.org-base: dependency problems - leaving unconfigured
E: openoffice.org: dependency problems - leaving unconfigured
E: openoffice.org-evolution: dependency problems - leaving unconfigured
E: openoffice.org-gtk: dependency problems - leaving unconfigured
E: openoffice.org-gnome: dependency problems - leaving unconfigured
E: openoffice.org-common: dependency problems - leaving unconfigured
E: openoffice.org-java-common: dependency problems - leaving unconfigured
E: openoffice.org-filter-mobiledev: dependency problems - leaving unconfigured
E: openoffice.org-style-human: dependency problems - leaving unconfigured


I have tried installing the package in terminal and I attach the log of the failed install process.

Leebobs

---

