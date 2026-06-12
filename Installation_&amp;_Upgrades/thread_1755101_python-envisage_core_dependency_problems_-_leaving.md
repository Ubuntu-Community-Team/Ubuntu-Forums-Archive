---
title: "python-envisage core: dependency problems - leaving unconfigured"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by sgwebb on 2011-05-10
I have upgraded from 10.04 to 10.10, then to 11.04, and had all kinds of problems in 11.04, just when I thought things were getting better I am now getting this error message when ever I try to install / uninstall any program, I currently can not get my windows to function correctly (I am missing the top bar), I really need to uninstall compiz and reinstall it..

The error I am getting is:

E: python-enthoughtbase: subprocess installed post-installation script returned error exit status 1
E: python-envisagecore: dependency problems - leaving unconfigured
E: python-envisageplugins: dependency problems - leaving unconfigured

I was going to try to uninstall python and re-install it but it will uninstall most of my programs. I have tried to install python all and python 3.1 the same error occurs

Any suggestions?

---

### Post by sgwebb on 2011-05-10
I think I solved this, for now.. 

I have removed the package python-enthoughtbase, and I am now able to install and uninstall programs..

I also found a bug for this same issue:
[https://bugs.launchpad.net/ubuntu/+source/python-enthoughtbase/+bug/777095](https://bugs.launchpad.net/ubuntu/+source/python-enthoughtbase/+bug/777095)

---

