---
title: "ubuntu 10.10 beta upgrade error"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by ajithvisu on 2010-09-06
Folks

when doing sudo do-release-upgrade -d after downloading all packages and installing some of them i am getting this error


Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 5, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 21, in <module>
    import apt_pkg
ImportError: libapt-pkg.so.4.10: cannot open shared object file: No such file or directory

Has anyone faced this error?

---

### Post by ajithvisu on 2010-09-06
After searching thru the forums i did the following and seems to have done the trick.

sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade

---

