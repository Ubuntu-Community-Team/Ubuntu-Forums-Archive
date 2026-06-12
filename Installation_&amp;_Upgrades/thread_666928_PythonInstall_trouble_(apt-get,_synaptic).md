---
title: "Python/Install trouble (apt-get, synaptic)"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by pxrox on 2008-01-13
Trouble w/ error message on login:  "The panel encountered a problem while loading "OAFIIDeskbar_Applet". Following several suggestions on the forum ([http://ubuntuforums.org/showthread.php?t=608767](http://ubuntuforums.org/showthread.php?t=608767) and [http://ubuntuforums.org/showpost.php?p=3907202](http://ubuntuforums.org/showpost.php?p=3907202)), I tried uninstalling/reinstalling deskbar-applet & related applets:

```
aptitude search applet | more
aptitude reinstall [any applet preceded by a v or an i in previous step]
```

This didn't work, AND I started getting python errors w/ synaptic or apt-get. I tried to get rid of the deskbar-applet entirely, and then reinstalled python:

```
sudo apt-get purge deskbar-applet
sudo apt-get --reinstall install python2.5-minimal
sudo apt-get --reinstall install python2.5
```

got my python working again:

```
>>> python
Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>>
```

[B]
BUT[/B], I still get python errors (Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]) on trying to install the deskbar-applet (see below).

What is wrong???

```
>>>sudo apt-get install deskbar-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  python-beagle python-soappy libdeskbar-tracker
The following NEW packages will be installed:
  deskbar-applet
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 318kB of archives.
After unpacking 3572kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy-updates/main deskbar-applet 2.20.1-0ubuntu1 [318kB]
Fetched 318kB in 0s (363kB/s)          
Selecting previously deselected package deskbar-applet.
(Reading database ... 105723 files and directories currently installed.)
Unpacking deskbar-applet (from .../deskbar-applet_2.20.1-0ubuntu1_i386.deb) ...
Setting up deskbar-applet (2.20.1-0ubuntu1) ...
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/py_compilefiles", line 3, in ?
    import os
ImportError: No module named os
pycentral: pycentral pkginstall: error byte-compiling files (68)
pycentral pkginstall: error byte-compiling files (68)
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 deskbar-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

