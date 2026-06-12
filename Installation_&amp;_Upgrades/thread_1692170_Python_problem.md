---
title: "Python problem"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by Setebos5 on 2011-02-21
Hey guys,

I have been getting python-related error messages whenever i try to install a new program (no matter with synaptic or by running in terminal). I operate on 10.10 kernel and recently installed KDE hoping it would bring some changes (did not happen). The latest error msg is:

E: python-problem-report: subprocess installed post-installation script returned error exit status 1
E: python-apport: dependency problems - leaving unconfigured
E: apport: dependency problems - leaving unconfigured
E: apport-gtk: dependency problems - leaving unconfigured
E: apport-kde: dependency problems - leaving unconfigured 

Anyone has an idea? Any help is deeply appreciated!

Thanks :)
S

---

### Post by deconstrained on 2011-02-21
Not sure if it's related, but do you have the package python-apport-utils installed? That conflicts with python-apport, according to the results I got from 'apt-cache show python-apport', so if you do have it installed you'll need to uninstall it first.

---

