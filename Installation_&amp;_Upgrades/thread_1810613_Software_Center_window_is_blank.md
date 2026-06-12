---
title: "Software Center window is blank"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by yelvington on 2011-07-23
Fresh Natty install, Acer Aspire One 722. Overall, the most painful Ubuntu experience in years, probably due to package upgrade failures on the USB stick. 

Sorted through those and the system now works ... except for Software Center, which opens a blank window.

No errors are logged.

If I launch software-center manually from a root shell, it populates the window probably and will install packages.

The user has all permissions and is an administrator.

Synaptic works, but I don't want my wife trying to use that beast.

---

### Post by raja.genupula on 2011-07-23
[http://ubuntuforums.org/showthread.php?t=1452316](http://ubuntuforums.org/showthread.php?t=1452316)

---

### Post by mon_r on 2011-07-28
Hi, I have similar problems. Every other software I'm using is working. I checked the file:
 ~/.cache/software-center/software-center.log
and found some errors:

2011-07-27 22:22:17,969 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 142, in open
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3458, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2011-07-27 22:22:17,986 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 154, 'open')'
2011-07-27 22:22:17,986 - root - WARNING - failed to add sca db Couldn't stat '/home/mon/.cache/software-center/software-center-agent.db' (No such file or directory)
2011-07-27 22:22:19,243 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-07-27 22:22:19,243 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
2011-07-27 22:22:19,429 - softwarecenter.view.catview - WARNING - sort by cataloged time requested but your a-x-i does not seem to support that yet
2011-07-27 22:22:28,212 - softwarecenter.app - INFO - software-center-agent finished with status 0
2011-07-27 22:22:28,213 - softwarecenter.db - ERROR - failed to add apt-xapian-index
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/database.py", line 142, in open
    axi = xapian.Database("/var/lib/apt-xapian-index/index")
  File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3458, in __init__
    _xapian.Database_swiginit(self,_xapian.new_Database(*args))
DatabaseOpeningError: Couldn't stat '/var/lib/apt-xapian-index/index' (No such file or directory)
2011-07-27 23:15:34,563 - softwarecenter.utils - WARNING - could not load icon '_usr_share_pixmaps_timidity', displaying missing icon instead: Icon '_usr_share_pixmaps_timidity' not present in theme 
2011-07-27 23:15:35,840 - softwarecenter.utils - WARNING - could not load icon '_usr_share_pixmaps_timidity', displaying missing icon instead: Icon '_usr_share_pixmaps_timidity' not present in theme 
2011-07-28 09:28:22,269 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.7/zeitgeist/client.py', 367, 'reconnect_monitors')'
2011-07-28 09:28:22,268 - zeitgeist.client - INFO - Reconnected to Zeitgeist engine...
2011-07-28 09:28:25,214 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/models/appstore.py', 305, '_blocking_perform_search')'
2011-07-28 09:28:25,214 - root - ERROR - get_mset
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/models/appstore.py", line 302, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
DatabaseCorruptError: Data ran out unexpectedly when reading posting list.
2011-07-28 09:28:27,753 - softwarecenter.app - INFO - software-center-agent finished with status 1


I tried this and didn't work:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update

Also tried reinstalling via Synaptic by searching for the software center and marking it for re-installation and it didn't work.

Last time I was able to use it was before some upgrade and installation of some programs. And before that, the OS crashes a lot during copying of backup files.

Tried searching but only found BugTrackers in the results.

---

### Post by mon_r on 2011-07-28
Don't know why, but a restart later. And it worked.

---

