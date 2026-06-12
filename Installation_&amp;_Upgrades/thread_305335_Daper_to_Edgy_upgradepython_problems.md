---
title: "Daper to Edgy upgrade/python problems"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by DaveHartburn on 2006-11-23
I've just done the advised
gksu "update-manager -c"
to upgrade from Daper to Edgy, and all is not well!

It give a couple of errors via the graphical interface, so I went to the command line and did a
apt-get dist-upgrade

When doing this, I get the following report:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade...Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-app-install (0.2.21) ...
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 4, in ?
    import glob
ImportError: No module named glob
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Further packages which depend on gnome-app-install such as ubuntu-desktop also have problems.

I have made the situation slightly worse as I thought it would be a good idea to clear the apt.log before running this again, to make sure all the error messages were recent. Now nothing is being written to this log! (Note to self, just use tail -f).

Anyone any ideas on how to solve this? Is there something useful I could manually set $PYTHONHOME to before running apt-get again?

---

### Post by DaveHartburn on 2006-11-23
A little more information.

The problem is caused by /usr/sbin/update-app-install, which has the lines
```
import sys
import glob
import os
```

It is the 'import glob' which is having a problem.

```
ls -l /usr/lib/python2.4/glob.py
-rw-r--r-- 1 root root 1441 2006-10-11 22:51 /usr/lib/python2.4/glob.py

which python
/usr/bin/python
ls -l /usr/bin/python
lrwxrwxrwx 1 root root 9 2006-11-23 09:35 /usr/bin/python -> python2.4*

```

It looks like I am using the right version of python and the module is there. Any ideas why it can not be seen?

I've tried doing a 'dpkg-reconfigure python' which has had not effect.

I did have a copy of python in /usr/local/bin which could have been picked up during the upgrade, however that has now been removed and should not interfere.

---

### Post by Hadron Quark on 2007-08-03
Just a quick bump here as I have the same issue with feisty. Can anyone suggest a fix?

---

