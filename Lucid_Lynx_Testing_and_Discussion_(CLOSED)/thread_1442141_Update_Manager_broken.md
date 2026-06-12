---
title: "Update Manager broken"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jugney on 2010-03-29
Yesterday I ran the update manager and told it to install updates on my Beta 1. 

At some point, it threw an error I can't quite remember. Something about unable to commit? I remember the word "commit." After that, it looked like it was doing something, but after 45 minutes hadn't done anything else. 

On the next boot, I got: 

The filesystem Ubuntu contains errors, check forced. 

After which, nothing happened. I left it on all night to let fsck finish, but it didn't. 

However, running fsck from a live install worked. Now, back in 10.04, I ran dpkg --configure --pending for it to apply changes on the packages that had already been downloaded, and that worked for the most part, but I still had these errors:

```
dpkg: error processing capplets-data (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libgnome-window-settings1 (= 1:2.29.92-0ubuntu3); however:
  Version of libgnome-window-settings1 on system is 1:2.29.92-0ubuntu2.
 gnome-control-center depends on capplets-data (>= 1:2.29.92-0ubuntu3); however:
  Version of capplets-data on system is 1:2.29.92-0ubuntu2.
 gnome-control-center depends on capplets-data (<< 1:2.30); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 capplets-data
 gnome-control-center
```

I also cannot open update-manager anymore. I see these errors when trying to launch it from the terminal:

```
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 36, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 30, in <module>
    from apt.package import Package
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 42, in <module>
    import apt.progress.text
  File "/usr/lib/python2.6/dist-packages/apt/progress/__init__.py", line 32, in <module>
    from apt.progress.old import (CdromProgress, DpkgInstallProgress,
ImportError: cannot import name CdromProgress
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 53, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 19, in <module>
    import fileutils
  File "/usr/lib/python2.6/dist-packages/apport/fileutils.py", line 15, in <module>
    from packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 30, in <module>
    from apt.package import Package
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 42, in <module>
    import apt.progress.text
  File "/usr/lib/python2.6/dist-packages/apt/progress/__init__.py", line 32, in <module>
    from apt.progress.old import (CdromProgress, DpkgInstallProgress,
ImportError: cannot import name CdromProgress

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 36, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 30, in <module>
    from apt.package import Package
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 42, in <module>
    import apt.progress.text
  File "/usr/lib/python2.6/dist-packages/apt/progress/__init__.py", line 32, in <module>
    from apt.progress.old import (CdromProgress, DpkgInstallProgress,
ImportError: cannot import name CdromProgress

```

Any advice?

---

### Post by nanog on 2010-03-29
See my signature...in particular apt-get install -f.

---

