---
title: "Gutsy Install wont start."
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by reikoshea on 2007-11-27
I dont usually post on boards, but im STUMPED (and have been for a few weeks).

Gutsy will not install when I click the upgrade button.  I dont know anything about python, so I dont know what the heck this stuff means.

Any help is appreciated.


```

root@reikoshea-laptop:/tmp# gksu "update-manager -c"
warning: could not initiate dbus
extracting '/tmp/tmpOuFArV/gutsy.tar.gz'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 20, in <module>
    from problem_report import ProblemReport
  File "/var/lib/python-support/python2.5/problem_report.py", line 15, in <module>
    import bz2, zlib, base64, time, UserDict, sys, gzip
ImportError: /usr/lib/python2.5/lib-dynload/zlib.so: undefined symbol: inflateCopy

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1144, in open
    raise ReadError("file could not be opened successfully")
tarfile.ReadError: file could not be opened successfully

```

---

### Post by mike^_^ on 2007-11-28
have you tried upgrading to gutsy using aptitude?

---

### Post by reikoshea on 2007-11-28
when i do apt-get dist-upgrade it pretends that i just typed update and checks the sources...and then says completed.

---

### Post by PmDematagoda on 2007-11-28
Could you be please be a little more clearer with your problem, I read your posts and yet I cannot understand exactly what problems and error messages you have or get. If you can take the time to answer the questions given then we could advance further.

1) What is your problem? Be a little more specific.

2) Post what you have tried to fix the problem and what error messages you got when trying to do so.

---

### Post by reikoshea on 2007-11-30
Im trying to upgrade from fiesty to gutsy.

I ran gksu "update-manager -c" as root and clicked on the upgrade button in the manager application.

Then it came back with the stuff I posted above.

Ive run apt-get upgrade
Ive installed python 2.5 (from aptitude)
Ive uninstalled python 2.5 (from aptitude)
Then i built python from source

Ive gotten the same errors every time the install ran.

I had this same problem on Kubuntu, and I got it installed by running:

sudo aptitude install update-manager-core
sudo do-release upgrade

doing that on this ubuntu install returns this error:

```

reikoshea@reikoshea-laptop:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting '/tmp/tmplpXsa4/gutsy.tar.gz'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 20, in <module>
    from problem_report import ProblemReport
  File "/var/lib/python-support/python2.5/problem_report.py", line 15, in <module>
    import bz2, zlib, base64, time, UserDict, sys, gzip
ImportError: /usr/lib/python2.5/lib-dynload/zlib.so: undefined symbol: inflateCopy

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 45, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 160, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 98, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.5/tarfile.py", line 1144, in open
    raise ReadError("file could not be opened successfully")
tarfile.ReadError: file could not be opened successfully

```

Which is pretty similar to running it from the update manager.

---

### Post by reikoshea on 2007-12-16
bump.

---

### Post by gryphon01 on 2007-12-23
Check the file /tmp/tmplpXsa4/gutsy.tar.gz to make sure its actually what you think it is (note that this path will change each time you run the script).  It might not be a gzipped tar file at all, and that could be why it couldn't be processed as such.

One example of how this could happen is if you're behind a proxy server.  If that proxy server prevented you from downloading the file it may have displayed an html page describing the error or reason the file wasn't downloaded.  That html would be saved as the gutsy.tar.gz file.

I'd tell you how I know this, but you can probably guess  :)

---

