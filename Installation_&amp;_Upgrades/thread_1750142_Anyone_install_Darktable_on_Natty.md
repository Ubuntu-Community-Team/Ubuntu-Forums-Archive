---
title: "Anyone install Darktable on Natty?"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by raptor170 on 2011-05-05
I have tried to install Darktable on natty with no avail, i have added the ppa's to the software sources but i keep getting this error in the software center

Dependency is not satisfiable: darktable (= 0.8-0pmjdebruijn3~natty)

hope to hear of some successful installs

thanks

---

### Post by dino99 on 2011-05-05
so you have used the "unstable" ppa, and it may have some issue(s) as its "unstable"

have you checked:
[http://blog.pcode.nl/2011/04/21/darktable-and-ubuntu-natty/](http://blog.pcode.nl/2011/04/21/darktable-and-ubuntu-natty/)
[http://darktable.sourceforge.net/install.shtml](http://darktable.sourceforge.net/install.shtml)

---

### Post by raptor170 on 2011-05-05
awesome i found out how to do it!
went to technical details for ppa then added the 2 ppa's
on [https://launchpad.net/~pmjdebruijn/+archive/darktable-unstable](https://launchpad.net/~pmjdebruijn/+archive/darktable-unstable)

then proceeded to [https://launchpad.net/~pmjdebruijn/+archive/darktable-unstable/+packages](https://launchpad.net/~pmjdebruijn/+archive/darktable-unstable/+packages)

and selected natty in list and chose
darktable_0.8+458~g9f5900e-0pmjdebruijn1~natty_amd64.deb

thanks for the link again!

---

### Post by PayPaul on 2012-03-01
I attempted to install the deb file for Natty in terminal with a sudo apt-get install command, opening a terminal in the folder the deb file was in and got the error message "Darktable command not found". What did I do wrong?

---

