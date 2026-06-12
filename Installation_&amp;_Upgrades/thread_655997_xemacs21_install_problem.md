---
title: "xemacs21 install problem"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by pjhong on 2008-01-02
hello, i'm new to ubuntu.  currently i've installed successfully ubuntu 7.10 desktop on a dell computer.  in synaptic package manager, i enabled universe and multiverse and i tried to mark "xemacs21-bin" but failed and got the following error dialog:

[title] could not mark all packages for installation or upgrade

xemacs21-bin:
 Depends: xemacs21-support but it is not going to be installed
 Depends: xemacs21 (= 21.4.20-1.1)

also, in terminal, i tried the following commands to install xemacs21-bin but got the same error.
> apt-get update
> apt-get -f install
> apt-get install xemacs21-bin

does anyone have any suggestions how i can resolve this issue?
thanks much in advance.
-paul

---

### Post by yabbadabbadont on 2008-01-02
Since you are trying to install it from the official repositories using synaptic (a supported method) and it doesn't work, file a bug against the package at [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

Hopefully, a developer will be able to give you a work around or an updated package.

---

### Post by pjhong on 2008-01-02
hello yabbadabbadont, thanks for your suggestion.  i just submitted my first bug report(Bug #179802).  do you know if i will be contacted via e-mail when they have a solution?
thanks again -paul

---

### Post by jpkotta on 2008-01-02
I installed just xemacs21, and it pulled in all the dependencies, including xemacs21-bin.

---

### Post by pjhong on 2008-01-02
hello jpkotta,
did you install from a terminal or the synaptic package manager?
if from a terminal, what command(s) did you run?
if from the synaptic package manager, were you able to mark xemacs21 successfully?  i  did  try to mark xemacs21 but i could not mark it along with its dependencies.  the error says 'unresolved dependencies'...
thanks much in advance for your help.
-paul

---

