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
```I cannot find any reference to a gtkwidgets module, so I don't know what it is talking about. I don't really want to reinstall software-center or software-properties-gtk because ubuntu-desktop depends on them as well as some other things that make it too much to download right now. If it it really necessary and safe I can manage it in a few days

Oh, and this is rather important because software-center does not open after this message.

---

### Post by Crazedpsyc on 2010-11-10
Bump Bumpadee Bump Bump. Bump Bump!

---

### Post by dino99 on 2010-11-10
i never use that buggy thing, only use synaptic

---

### Post by Crazedpsyc on 2010-11-10
I use synaptic most of the time too (apt-get is pretty close to the top), but I still like to use the software center sometimes. Especially now that it has replaced gdebi as the deb installer. I can still use sudo dpkg --install, but I would rather use the software-center

---

### Post by sikander3786 on 2010-11-12
Similar thread. Might help...

[http://ubuntuforums.org/showthread.php?p=8646848](http://ubuntuforums.org/showthread.php?p=8646848)

Also check if you've enable any PPAs from Software Sources > Other Software Tab and try to disable all of them and try again.

---

### Post by Crazedpsyc on 2010-11-12
Both solutions in that thread are a little off of what I need. the one that looked the best (downgrading libsoup and libwebkit) could be pretty bad because the packages it lists are for karmic. I use maverick. The other solution there didn't work because synaptic wouldn't let me downgrade those packages. looked like it was going to but when it came back from the cursor-spinning gray stage the package was still unmarked
I disabled all my 20+ ppas and tried software-center again and still got the same error

---

### Post by Crazedpsyc on 2010-11-15
bump

---

### Post by Crazedpsyc on 2010-11-17
Bump.

---

### Post by Crazedpsyc on 2010-11-24
bump

---

### Post by Crazedpsyc on 2010-12-02
BbUuMmPp

---

### Post by Crazedpsyc on 2010-12-14
I even reinstalled both software-center and python-aptdaemon-gtk, but still no luck.

---

### Post by Crazedpsyc on 2011-03-04
It actually fixed itself by updating! But a little more info: It worked for other users, so it must have been a config issue.

---

