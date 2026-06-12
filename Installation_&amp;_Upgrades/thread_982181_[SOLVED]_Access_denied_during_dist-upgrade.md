---
title: "[SOLVED] Access denied during dist-upgrade"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by gwi on 2008-11-14
Doing a "sudo update-manager -d" leads to the following:
```
~$ sudo update-manager -d
extracting 'intrepid.tar.gz'
authenticate 'intrepid.tar.gz' against 'intrepid.tar.gz.gpg' 
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 959, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 220, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py", line 53, in runDistUpgrader
    os.execv(self.script,[self.script]+self.run_options)
OSError: [Errno 13] Access denied
```

What is wrong here? A listing of the directory in the error message shows:
```
~$ ls -l /usr/lib/python2.5/site-packages/UpdateManager
totaal 192
-rw-r--r-- 1 root root  9212 2008-04-28 15:44 ChangelogViewer.py
-rw-r--r-- 1 root root  6825 2008-08-13 19:14 ChangelogViewer.pyc
drwxr-xr-x 2 root root  4096 2008-08-13 19:14 Common
drwxr-xr-x 2 root root  4096 2008-08-13 19:14 Core
-rw-r--r-- 1 root root  4512 2008-04-28 15:44 DistUpgradeFetcher.py
-rw-r--r-- 1 root root  3635 2008-08-13 19:14 DistUpgradeFetcher.pyc
-rw-r--r-- 1 root root  1818 2008-04-28 15:44 fakegconf.py
-rw-r--r-- 1 root root  3236 2008-08-13 19:14 fakegconf.pyc
-rw-r--r-- 1 root root  8700 2008-07-31 09:14 fdsend.so
-rw-r--r-- 1 root root  4753 2008-04-28 15:44 GtkProgress.py
-rw-r--r-- 1 root root  4493 2008-08-13 19:14 GtkProgress.pyc
-rw-r--r-- 1 root root     1 2008-04-28 15:44 __init__.py
-rw-r--r-- 1 root root   145 2008-08-13 19:14 __init__.pyc
-rw-r--r-- 1 root root  2234 2008-04-28 15:44 MetaReleaseGObject.py
-rw-r--r-- 1 root root  1700 2008-08-13 19:14 MetaReleaseGObject.pyc
-rw-r--r-- 1 root root  7244 2008-04-28 15:44 ReleaseNotesViewer.py
-rw-r--r-- 1 root root  5898 2008-08-13 19:14 ReleaseNotesViewer.pyc
-rw-r--r-- 1 root root 41569 2008-06-20 19:15 UpdateManager.py
-rw-r--r-- 1 root root 37783 2008-08-13 19:14 UpdateManager.pyc
```

---

### Post by gwi on 2008-11-16
Solved my own question: the script DistUpgradeFetcher.py wants to start another script. It uses gksudo for that, unless DistUpgradeFetcher.py was started with uid 0 (which appears to be the case when update-manager was started with sudo).
In that case the script to be started is started with the same uid that did the "sudo update-manager", and that uid does not have the required permission.

Conclusion: **don't** start update-manager with sudo!

---

