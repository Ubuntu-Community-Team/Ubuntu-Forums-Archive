---
title: "Software center issues after upgrading from 9.04 to 9.10"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by thyplo101 on 2009-11-28
I upgraded the system, and it worked fine. However, during the upgrade, the computer gave me some errors that I ignored, and the installation completed. Everything works except for the software center. In the applications menu, it still shows up as 'add/remove programs', and that and synaptic show errors whenever I try to run them. Basically, I can't acess any method of installing software. 
I tried to start software-center through the terminal, but this is what I got:

saad@saad-laptop:~$ software-center
INFO:root:building local database
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 108, in __init__
    rebuild_database(pathname)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 200, in rebuild_database
    cache = apt.Cache(memonly=True)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 72, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 108, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.
saad@saad-laptop:~$

---

### Post by lemming465 on 2009-11-29
The first thing I'd try is to open a terminal window and do some command line package maintenance.```

sudo -i
aptitude clean
aptitude update
aptitude full-upgrade -f
```
If you get errors from that, see if you can open the *System -> Administration -> Software Sources* dialog and check if the karmic repositories are enabled.  If that doesn't work either, you may have to do some hand editing in /etc/apt/soures.list and possibly under /etc/apt/sources.list.d to straighten out the repository situation first.

---

