---
title: "Python hosed. Package manager broken."
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Hadron Quark on 2007-08-03
Something has corrupted my python setup. Please help if you know how to fix my python install or my system is useless :( When trying to install (for example) iPython I get the following (note the import site failed part ):

hadron@ubuntu:/usr/local/lib$ sudo apt-get install ipython
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ipython is already the newest version.
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0B/1088kB of archives.
After unpacking 0B of additional disk space will be used.
(Reading database ... 264535 files and directories currently installed.)
Preparing to replace ipython 0.7.3-1 (using .../ipython_0.7.3-1_all.deb) ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error processing /var/cache/apt/archives/ipython_0.7.3-1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 3, in <module>
    import fnmatch, glob, os, re, sys, time
ImportError: No module named fnmatch
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ipython_0.7.3-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zanglang on 2007-08-03
Looks like your Python install is missing/broken? Site.py and fnmatch.py should come with 'python2.5-minimal', try reinstalling it with
> sudo aptitude reinstall python2.5-minimal
and see if that fixes it.

---

### Post by Hadron Quark on 2007-08-03
No - because nothing is working.

Can someone tell how to set PYTHONHOME and what I should set it to?

---

