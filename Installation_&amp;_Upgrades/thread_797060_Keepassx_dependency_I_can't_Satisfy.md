---
title: "Keepassx dependency I can't Satisfy"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by clydebarrow on 2008-05-16
Longtime computer user, but new to Ubuntu and Linux.

Got Heron running on a trusty old IBM T42.

Now I want to add Keepass as I use that on my Windows box.

Got the Ubuntu Heron Keepassx .DEB file from the Keepassx website. Executed the Package Installer.

Get Error: Dependency is not satisfiable: libqt4-core.

How do I check to find out what I need (a newer version? just not installed? I dunno...) and fix this?

---

### Post by mahuyar on 2008-05-16
The fastest way, I guess, is to fire up your terminal.
Applications > Accessories > Terminal

Type in the following:
```
 sudo apt-get -f install 
```

Now, you'll be asked to enter your password.  Type it in and hit ENTER (Don't worry about your password not showing up as you type it, since it's obscured for security reasons.)

Watch some lines fly by, and you should be set.

In case you cannot find the application shortcut in your menu, press Alt+F2 and type in keepassx.

EDIT:  The command above takes care of the dependencies for a deb package.  Most of the time it'd work.  :)

---

### Post by clydebarrow on 2008-05-16
That's it. Thanks!

---

