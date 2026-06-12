---
title: "Can packages be installed offline"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by Mic on 2005-07-11
Wanted to install Ubuntulinux but noticed that some of the packages may not be available/updated.

The problem is I do not have broadband and packages have to be downloaded with the help from a friend.

Can packages (e.g. firefox1.0.4, openoffice2, scim) be downloaded and installed offline?

What is the procedure like?

Many thanks in advance for the advice.

---

### Post by manicka on 2005-07-11
You just download them to a  cd or whatever and then run in the directory that contains the package

sudo dpkg -i *packagename*

dependencies will be your biggest problem. The ubuntu packages site can help you out with those. [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

