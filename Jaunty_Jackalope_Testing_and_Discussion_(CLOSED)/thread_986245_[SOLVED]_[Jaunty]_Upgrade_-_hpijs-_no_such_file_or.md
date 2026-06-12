---
title: "[SOLVED] [Jaunty] Upgrade - hpijs- no such file or directory"
date: 2008-11-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-11-18
Just performed an upgrade of Jaunty via terminal. Is this a bug ?
```
Installing new version of config file /etc/hp/hplip.conf ...
Creating/updating hplip user account...

Setting up hpijs (2.8.10-0ubuntu2) ...
grep: *.ppd: No such file or directory
grep: *.ppd: No such file or directory

Setting up liblockfile1 (1.08-3) ..
```.
The updates are coming thick and fast...

---

### Post by ShirishAg75 on 2008-11-18
most probably yes, you could check out [lpbug]299542[/lpbug]

---

### Post by Kevbert on 2008-11-18
Thanks. Looks like another bug in the same package as your one. Mine's on the 64 bit package/architecture.  Had a quick look at your logs and there seems to be one or two problems that have already been reported (eg font problems). What versions of *buntu are you running ? It looks like you have some KDE and XFCE packages installed.

---

### Post by ShirishAg75 on 2008-11-18
I have XFCE-desktop fully and yes, few kde packages (KDE has always seemed buggy for me, it always pulls in lots of stuff) and GNOME. XFCE is just in case Ubuntu goes out for a walk or something .

---

### Post by Kevbert on 2008-11-19
KDE seems to be a bit more buggy for me also.  It's my impression that more development is made on Gnome (Ubuntu) when compared to KDE (loads more bugs in Kubuntu). XFCE/Xubuntu seems pretty good and solid though.
I'll raise a new bug report today - so that the developers are aware and at least it can be closed if its not a problem.

---

### Post by Kevbert on 2008-11-20
This bug has been fixed with 2.8.10-0ubuntu3.

---

