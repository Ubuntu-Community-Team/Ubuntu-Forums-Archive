---
title: "Unresolvable dependency when installing python-mlt5 on Ubuntu 14.04"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by xxlray on 2014-07-24
My latest Ubuntu 14.04 update brought up an unresolvable dependency when trying to install python-mlt5

```
sudo apt-get install python-mlt5 -f
...
The following packages have unmet dependencies:
 python-mlt5 : Depends: libmlt++3 but it is not going to be installed
```

```
sudo apt-get install libmlt++3
...
sudo apt-get install python-mlt5 -f
...
The following packages have unmet dependencies:
 python-mlt5 : Depends: libmlt5 but it is not going to be installed
...
sudo apt-get install libmlt5
...
Removing libmlt++3 (0.9.0-3) ...
Removing libmlt6 (0.9.0-3) ...
...
sudo apt-get install python-mlt5 -f
...
The following packages have unmet dependencies:
 python-mlt5 : Depends: libmlt++3 but it is not going to be installed
```

Any idea how to get this fixed???

---

### Post by ian-weisser on 2014-07-24
The python-mlt5 packages seems to have been replaced by the python-mlt package after 13.10.
14.04 does not have a python-mlt5 package in the Ubuntu repositories.

Try installing python-mlt instead of python-mlt5

---

### Post by xxlray on 2014-07-24
Thanks for the answer. Installation of python-mlt worked. Unfortunately the application that needs mlt (Openshot) still doesn't work. I will have to ask them.

---

### Post by ian-weisser on 2014-07-24
Are you installing from a PPA or other non-Ubuntu repository?

In the 14.04 Ubuntu repos:
```
$ apt-cache show openshot | grep Depends
Depends: gtk2-engines-pixbuf, fontconfig, librsvg2-common, melt, python-gtk2, python-httplib2, python-imaging, **python-mlt | python-mlt5 | python-mlt2**, python-pygoocanvas, python-xdg, python (>= 2.5), python-support (>= 0.90.0)
```
'|' means 'or', so any of those three packages should work.
Of those three, only python-mlt is in the Ubuntu repos. But that should be adequate to install.

---

### Post by xxlray on 2014-07-25
Openshot is used from the official bazaar repository and mlt from the Ubuntu repositories.

---

### Post by Vladlenin5000 on 2014-07-25
> **xxlray said:**
> Openshot is used from the official bazaar repository and mlt from the Ubuntu repositories.

Install from the software center.

---

### Post by xxlray on 2014-07-25
The Openshot version from the Ubuntu repository is unfortunately outdated and unstable and the bazaar version worked right before the update.

---

