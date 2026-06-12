---
title: "[SOLVED] python2.5 through recomended updates fails"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by Kramxel on 2008-03-11
I'm using Ubuntu 6.10 Edgy

The option to install python2.5 python2.5-dev and python2.5-minimal fails....

It showed up as an automatic update and the install fails with the current message:

> E: python2.4-minimal: subprocess post-installation script returned error exit status 1

As far as I know python2.4 was already installed....


The real problem with this is  since it can not install that 3 packages, every time I try installing something else, it fails on that package, without installing anything else....

Help me...


Some extra info:

> 
xxxxx@xxxxx-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gdm
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python2.4-minimal (2.4.4~c1-0ubuntu1.1) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-setuptools: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
pycentral rtinstall: package python-setuptools: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4~c1-0ubuntu1.1); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-dev:
 python2.4-dev depends on python2.4 (= 2.4.4~c1-0ubuntu1.1); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
 python2.4-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2008-03-11
```
sudo dpkg --configure -a
```

---

### Post by Kramxel on 2008-03-11
sudo dpkg --configure -a

returns:

> Setting up python2.4-minimal (2.4.4~c1-0ubuntu1.1) ...
Linking and byte-compiling packages for runtime python2.4...
pycentral: pycentral rtinstall: package python-setuptools: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
pycentral rtinstall: package python-setuptools: already exists: /usr/lib/python2.4/site-packages/setuptools.pth
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.4~c1-0ubuntu1.1); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-dev:
 python2.4-dev depends on python2.4 (= 2.4.4~c1-0ubuntu1.1); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
 python2.4-dev


Still no good....

---

### Post by Kramxel on 2008-03-11
I've seen a lot of people have problems with the python packages.... mostly due to pycentral....

My problem was the existance of a previous file called "setuptools.pth" due to previous installations of python... the solution is to remove that file....

It seems the python2.5 update will reinstall the 2.4 version... so when he checks for previous files there's already that one....

cuting short my solution was:
```

sudo rm /usr/lib/python2.4/site-packages/setuptools.pth
```

Thread can be closed now.
Thanks anyways.

---

