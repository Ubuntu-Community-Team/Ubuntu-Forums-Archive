---
title: "Can't remove broken python-setuptools package"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by danzinho on 2007-01-24
Hi

A python package that I was trying to install required distutils.core which apparently isn't part of the standard Ubuntu distribution.  Via synaptic I tried to install several packages including python-dev and python-setuptools.  For the first time with Synaptic there were problems resulting in incompletely installed packages.  After trying 

sudo apt-get -f install

I'm still left with a single (I think) problem.  Basically I can't get rid of python-setuptools.

daniel@adenine $ sudo apt-get remove python-setuptools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-setuptools
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  python-setuptools
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 758kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121381 files and directories currently installed.)
Removing python-setuptools ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in ?
    import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing python-setuptools (--remove):
 subprocess pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in ?
    import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-setuptools
E: Sub-process /usr/bin/dpkg returned an error code (1)


I've read around and I understand that there is probably a problem with the scripts that came with the package.  Is it possible to do a 'manual deinstall'?  I can remove all the files in 

/var/lib/dpkg/info/python-setuptools.list

but will the system then automatically remove the package from its master list?

I've spent a lot of time on this so any help very much appreciated.

Daniel

---

