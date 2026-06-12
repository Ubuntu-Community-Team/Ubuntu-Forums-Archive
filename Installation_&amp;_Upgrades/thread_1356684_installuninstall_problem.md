---
title: "install/uninstall problem"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by vicky1988 on 2009-12-16
i had downloaded the ubuntu 9.10.i already installed windows xp.i am trying to install dual os.after that i install ubuntu in F: Partiton. after that i mentioned the installation drive and installation size and user name and password.In installation it open one downloaded window box.suddenly i got power cut before the installation finished.when i am trying to reinstall ubuntu it says some error of **_[FONT="Arial Black"](There is another file or directory with this file name please remove it before continuing)[/FONT]_**.please help me to remove the error and help install ubuntu again.

---

### Post by khelben1979 on 2009-12-16
I would suggest you start all over again and doing a full reinstallation of Ubuntu.

---

### Post by darkod on 2009-12-16
> **vicky1988 said:**
> i had downloaded the ubuntu 9.10.i already installed windows xp.i am trying to install dual os.after that i install ubuntu in F: Partiton. after that i mentioned the installation drive and installation size and user name and password.In installation it open one downloaded window box.suddenly i got power cut before the installation finished.when i am trying to reinstall ubuntu it says some error of **_[FONT=Arial Black](There is another file or directory with this file name please remove it before continuing)[/FONT]_**.please help me to remove the error and help install ubuntu again.

You are not trying to install full ubuntu, but wubi. You can not install full ubuntu from inside windows. If it's asking to select drive letter and size, that's wubi. It will run from inside windows.
If this is what you want, first go in add/remove programs and see if there is ubuntu entry inside. If there is, try to uninstall it like any other windows app. After the interrupted wubi is removed, try again.
If you would like to install full ubuntu, you need to boot from the cd (not put the cd inside with windows already running).

---

