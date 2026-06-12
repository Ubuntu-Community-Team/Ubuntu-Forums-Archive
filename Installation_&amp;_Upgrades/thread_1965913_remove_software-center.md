---
title: "remove software-center"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by th00ht on 2012-04-26
In order to save space on my EeePC901 i need to remove all the surplus bloath from xubuntu. One thing I never use is Ubuntu Software Center. I have synaptic apt-get and dpkg to (un) install things.
When I attempt to uninstall it with synaptic it suggests that it will also remove xubunut-desktop. Actually I probably want to keep xubuntu-desktop but only remove Ubunut Software Center.

How do I uninstall Ubuntu Software Center and the additional database(s) it uses?

---

### Post by LewisTM on 2012-04-27
Removing xubuntu-desktop metapackage won't do anything. It just means that since the Software Center is part of the xubuntu-desktop package collection, removing it will make the metapackage incomplete and that forces an uninstall. This won't cascade down to the individual Xubuntu packages so you are safe.

It's sort of symbolic. It means that if you later want to restore all the missing default Xubuntu packages you can just reinstall xubuntu-desktop.

Cheers!

---

### Post by Jose Catre-Vandis on 2012-04-29
First thing I did when I installed 12.04 was remove the slow, ponderous and useless Software Center :)  Didn't break anything.

---

### Post by sparklyprgs on 2012-04-30
As it mentions in Synaptic for xubuntu-desktop:

It is safe to remove this package if some of the desktop system packages are
not desired.

It's safe - remove it! :-)

---

