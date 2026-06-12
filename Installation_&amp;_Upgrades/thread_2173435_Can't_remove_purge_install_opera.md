---
title: "Can't remove/ purge /install opera"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by Keith_Capel on 2013-09-09
I have a bug of sorts. Opera is holding up any upgrades??

I have tried anything I know beside reinstalling the box.
I've tried to remove / purge from your system.

devbox01 k # sudo dpkg --configure -a
devbox01 k # sudo apt-get --fix-broken install

does nothing

devbox01 k # sudo apt-get purge opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  opera
0 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
1 not fully installed or removed.
After this operation, 46.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 441715 files and directories currently installed.)
Removing opera ...
ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 198, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 173, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named linuxmint
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 38, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 33, in <module>
    from softwarecenter.backend.scagent import SoftwareCenterAgent
  File "/usr/share/software-center/softwarecenter/backend/scagent.py", line 28, in <module>
    from softwarecenter.distro import get_distro, get_current_arch
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 198, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 173, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named linuxmint
dpkg: error processing opera (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 opera
E: Sub-process /usr/bin/dpkg returned an error code (1)
devbox01 k # 

Any ideas?

---

### Post by bapoumba on 2013-09-09
How did you install Opera ?

---

