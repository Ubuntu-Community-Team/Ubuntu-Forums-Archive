---
title: "install package without tetex-dependencies"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by buschi on 2007-06-18
hi everyone!

i am running feisty with texlive 2007 (i.e. i do *not* want to install tetex or texlive 2005). however, i would like to install matplotlib, saying

```
sudo aptitude install python-matplotlib
```

resulting in

```
The following NEW packages will be automatically installed:
  blt dvipng perl-tk psutils python-dateutil python-dev python-matplotlib-data python-tk python-tz python2.5-dev tcl8.4 tetex-base tetex-bin tetex-doc 
  tex-common tk8.4 
```

can i prevent the installation of tetex? it seems to be the package dvipng which looks for tetex (or texlive 2005). i installed everything else step by step with aptitude, now only dvipng and python-matplotlib are left over.

thanks a lot for any help,
sebastian.

---

### Post by buschi on 2007-06-25
ok, i have now two tex-distributions on my computer -- but probably this would have been a solution:
[http://ubuntuforums.org/showpost.php?p=1256039&postcount=9]("http://ubuntuforums.org/showpost.php?p=1256039&postcount=9")

---

