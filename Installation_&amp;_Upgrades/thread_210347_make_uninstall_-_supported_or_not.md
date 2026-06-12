---
title: "make uninstall - supported or not ?"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by Vilius on 2006-07-06
Hi,
How to know my source files support "make uninstall" or not ?
Some guy told me to check if Makefile has "uninstall" target.
How to do that ?

thanks 
Vilius

---

### Post by kewldude606 on 2006-07-06
It depends on the application.  Just try sudo make uninstall and if it works, then it is supported.

---

### Post by Vilius on 2006-07-06
I don't want to install if uninstall is not supported.
I want to check before install.

---

### Post by mvaniersel on 2006-07-06
try this:

sudo make -n uninstall

the -n switch will cause make to do a dry run, showing you the steps it will take, but not actually doing any of them.

---

### Post by FredB on 2006-07-07
Or you can look at the Makefile and search for uninstall options. Maybe the simplest and more direct way to know if uninstall is supported or not.

Just an idea, eh !

---

### Post by 5-HT on 2006-07-09
Are you familiar with 'checkinstall'?
Using checkinstall instead of 'make install' will create a .deb (sort of) out of the source and install it for you.
When you want to uninstall you can use dpkg/apt/aptitude/etc...

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
[]("https://help.ubuntu.com/community/forum/software/CheckInstall")

---

