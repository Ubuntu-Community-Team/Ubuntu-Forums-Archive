---
title: "problem with gwibber"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by k7rata121 on 2010-03-26
i istalled lucid beta 1 to do some testing and everything works fine here exept gwibber application

it is not working at all !

everytime i start it, gives the report message , i reported the bug and installed all the updates but the problem still there,

when i searched i found that he worked in some machines so i thought the problem is for me only

i started the program from the terminal and this is what i got

```

hassan@vertex-desktop:~$ gwibber

** (gwibber:5051): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:5051): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:5051): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Removing stale, deceptive pid file.
Apache CouchDB has started, time to relax.
ERROR:root:Unable to find file descriptors in /proc/5155
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 86, in __find_port__linux
    for dirent in os.listdir(fd_dir):
OSError: [Errno 2] No such file or directory: '/proc/5155/fd'
Traceback (most recent call last):
  File "/usr/bin/gwibber", line 67, in <module>
    client.Client()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 441, in __init__
    self.w = GwibberClient()
  File "/usr/lib/python2.6/dist-packages/gwibber/client.py", line 28, in __init__
    self.model = gwui.Model()
  File "/usr/lib/python2.6/dist-packages/gwibber/gwui.py", line 42, in __init__
    self.settings = util.SettingsMonitor()
  File "/usr/lib/python2.6/dist-packages/gwibber/util.py", line 91, in __init__
    DEFAULT_SETTINGS)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/util/couch.py", line 64, in __init__
    self.database = CouchDatabase(dbname, create=True)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server.py", line 53, in __init__
    port = desktopcouch.find_port(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 51, in find_port
    return _direct_access_find_port(pid=pid, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 75, in __find_port__linux
    pid = find_pid(start_if_not_running=True, ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/__init__.py", line 35, in find_pid
    pid = start_local_couchdb.start_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 247, in start_couchdb
    pid, port = run_couchdb(ctx=ctx)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/start_local_couchdb.py", line 151, in run_couchdb
    raise RuntimeError("Couchdb PID%d exited.  Permissions?", pid)
RuntimeError: ('Couchdb PID%d exited.  Permissions?', 5155)
hassan@vertex-desktop:~$ 


```

what do you think??


NB: sorry for my bad english ..

---

### Post by zeroseven0183 on 2010-03-28
The people on [this thread]("http://ubuntuforums.org/showthread.php?t=1436969") are also having the same issue as yours.

Have you filed a bug report already? If not, please do so or link it to existing bugs.

---

