---
title: "meta-package lubuntu-core"
date: 2014-01-06
forum: Installation &amp; Upgrades
---

### Post by joao-m-santos-silva on 2014-01-06
I've just installed Lubuntu using the mini.iso for a minimal system and then installed lubuntu-core with apt-get.

lubuntu-core is a meta-package which is meant to install a Lubuntu core system.

Something I found strange is that it does not install lxterminal (but UXTerm and XTerm are installed), does anyone know why?

Also, lxappearence is not installed by default but some application for "Online Accounts" is. It seems more basic to have some tool to configure the appearence than to have "Online Accounts" (can't find the program/package name from the graphical interface, since there is no About menu).

---

### Post by ibjsb4 on 2014-01-07
Maybe you should leave off the recommended packages.

```
sudo apt-get install --no-install-recommends lubuntu-core
```

And welcome to the forums :)

Edit:

Another approach would be to install lxde-core with or without recommends.

[http://packages.ubuntu.com/saucy/lxde-core](http://packages.ubuntu.com/saucy/lxde-core)

---

