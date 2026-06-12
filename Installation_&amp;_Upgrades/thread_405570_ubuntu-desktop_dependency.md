---
title: "ubuntu-desktop dependency"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by Doughy on 2007-04-09
Today I tried to uninstall some stuff that I don't need.  The Ubuntu Add/Remove program would not allow me to uninstall some of these things because apparently the ubuntu-desktop depends on them.  I tried uninstalling in the synaptic package manager too, same thing.

Well, if I can't uninstall the games that I am never going to play, this is a bogus setup.  Why can't I just uninstall the games that I don't want?

---

### Post by aysiu on 2007-04-09
From [CommonQuestions on the Wiki](https://help.ubuntu.com/community/CommonQuestions#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812): > **What is a meta-package? Is it safe to remove the ubuntu-desktop package?**
A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information.

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade.


---

### Post by phenest on 2007-04-10
I have to agree with Doughy. Saying the ubuntu-desktop is a meta package is not a satisfactory answer. The user would have to uninstall ubuntu-desktop and then re-install all the components he wants that un-installing ubuntu-desktop has removed. And then, to perform a version upgrade, re-install ubuntu-desktop, perform the upgrade, un-install ubuntu-desktop, re-install the components that ...

I'm sorry, but there has to be a better way than this.

---

### Post by linear on 2007-04-11
> **phenest said:**
> The user would have to uninstall ubuntu-desktop and then re-install all the components he wants that un-installing ubuntu-desktop has removed. And then, to perform a version upgrade, re-install ubuntu-desktop, perform the upgrade, un-install ubuntu-desktop, re-install the components that ...

Removing ubuntu-desktop doesn't remove any other packages. (It depends on them, they don't depend on ubuntu-desktop.) You do have a point, that an upgrade will require you to re-install ubuntu-desktop along with other packages you removed.

---

