---
title: "software-center needs gtkwidgets module which is not found"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by Crazedpsyc on 2010-11-08
Whenever I try to run software-center I get this error:
```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    import softwarecenter.view.dependency_dialogs as dependency_dialogs
  File "/usr/share/software-center/softwarecenter/view/dependency_dialogs.py", line 25, in <module>
    from softwarecenter.backend import get_install_backend
  File "/usr/share/software-center/softwarecenter/backend/__init__.py", line 19, in <module>
    from aptd import AptdaemonBackend
  File "/usr/share/software-center/softwarecenter/backend/aptd.py", line 32, in <module>
    from aptdaemon.gtkwidgets import AptMediumRequiredDialog, \
ImportError: No module named gtkwidgets
```
I cannot find any reference to a gtkwidgets module, so I don't know what it is talking about. I don't really want to reinstall software-center or software-properties-gtk because ubuntu-desktop depends on them as well as some other things that make it too much to download right now. If it it really necessary and safe I can manage it in a few days
Oh, and this is rather important because software-center does not open after this message.

---

### Post by howefield on 2010-11-08
Closed duplicate thread.

[http://ubuntuforums.org/showthread.php?t=1616557](http://ubuntuforums.org/showthread.php?t=1616557)

---

