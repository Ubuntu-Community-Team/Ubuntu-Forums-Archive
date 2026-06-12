---
title: "Software center and update manager won't start"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by glasafmt on 2012-05-06
Hi

I'm using Ubuntu Studio (based on ubuntu 11.04) and I can't get the software center or the upgrade manager to start.  If I open the software center from the command line, I get this error:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 111, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 40, in <module>
    from softwarecenter.db.application import Application, DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/application.py", line 19, in <module>
    from apt.debfile import DebPackage
  File "/usr/lib/python2.7/dist-packages/apt/__init__.py", line 24, in <module>
    from apt.package import Package
  File "/usr/lib/python2.7/dist-packages/apt/package.py", line 42, in <module>
    import apt.progress.text
  File "/usr/lib/python2.7/dist-packages/apt/progress/__init__.py", line 32, in <module>
    from apt.progress.old import (CdromProgress, DpkgInstallProgress,
  File "/usr/lib/python2.7/dist-packages/apt/progress/old.py", line 35, in <module>
    from apt.progress import base, text
ValueError: bad marshal data (unknown type code)
```


and a very similar error when I try the update manager:

```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 40, in <module>
    import apt
  File "/usr/lib/python2.7/dist-packages/apt/__init__.py", line 24, in <module>
    from apt.package import Package
  File "/usr/lib/python2.7/dist-packages/apt/package.py", line 42, in <module>
    import apt.progress.text
  File "/usr/lib/python2.7/dist-packages/apt/progress/__init__.py", line 32, in <module>
    from apt.progress.old import (CdromProgress, DpkgInstallProgress,
  File "/usr/lib/python2.7/dist-packages/apt/progress/old.py", line 35, in <module>
    from apt.progress import base, text
ValueError: bad marshal data (unknown type code)
```

I've tried reinstalling the various individual parts (including python).  Anyone got any other suggestions as to what to try?

Thanks in advance.

Lee

---

### Post by Paddy Landau on 2012-05-07
Reinstalling will do nothing, as it simply installs the programs again. (Unlike Windows, there is no Registry to be reset.)

Try the following three commands in a terminal, in order, and tell us what happens. (If you post the results, please enclose the results within [noparse]```
[/noparse] and [noparse]
```[/noparse].)
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
```

---

### Post by glasafmt on 2012-05-07
I don't think they turned up anything of interest.  The first command told me that there were packages to remove (nothing related) and the third command told me about an issue with a public key on a ppa (which I added to the sources list after the update manager and software center stopped working).

I removed the packages, but the update manager is still giving the same error.

I can't be certain, but this could have happened when I installed the packages for Ubuntu Studio.  I didn't install Studio directly, I changed an existing Ubuntu installation to Studio.

---

### Post by Paddy Landau on 2012-05-07
I've [Googled your error]("https://www.google.com/search?q=ValueError%3A+bad+marshal+data+ubuntu+bug") and found several items, so I think you are not alone; but none of them that I saw pointed to anything that would be of use.

Unless someone else can respond here with better information, I think you may have to back up your data, reinstall, and restore. Perhaps install Ubuntu Studio if that's what you need.

Sorry I can't be of help.

---

