---
title: "error message in installation"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by kuang on 2005-06-06
Dear all,

I met some problems after I use a existant source.list and .txt to install the packages I need. I got the error message like this:

emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 9.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 speedbar

Later on, totally 7 packages are influences:

emacs21
auctex
cedet-common
debian-el
eieio
emacs-goodies-el
speedbar

Can you give me any suggestion about how to correct these problems?? Thank you very much.

kuang

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=kuang]Dear all,

I met some problems after I use a existant source.list and .txt to install the packages I need. I got the error message like this:

emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 9.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 speedbar

Later on, totally 7 packages are influences:

emacs21
auctex
cedet-common
debian-el
eieio
emacs-goodies-el
speedbar

Can you give me any suggestion about how to correct these problems?? Thank you very much.

kuang[/QUOTE]
 What happens if you just try to install emacs21, fotgetting for the time being about the rest?
Do you get an error message?

---

### Post by kuang on 2005-06-07
Yes, I also tried to just reinstall emacs21 instead. Try to solve this problem first, but it was the same result. Should I remove all the packages and reinstall all of them? I just had the system setup on Saturday. I really have no idea about this new system.

Thank you very much!

kuang

---

