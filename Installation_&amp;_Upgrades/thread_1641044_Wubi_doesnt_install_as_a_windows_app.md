---
title: "Wubi doesnt install as a windows app"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Lomok on 2010-12-08
Hi everyone
I've been using kubuntu from time to time, and one thing that i love was the option to install/uninstall as if it was another common windows application.

A few days ago, i downloaded the 10.10 release, and after i executed wubi, i just get 2 option:
Full demo and install
and learn more

So, am I doing something wrong?

BTW, i also run wubi with an ISO next to it, but it shows the same window.

So, is there a way to install kubuntu as a windows appa again???

I've tried google, but everything seems to point that that feature still exists, but i cant find it.

Thanks everyone!

---

### Post by bcbc on 2010-12-08
Use wubi.exe from here: [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

Place it in the same folder as your downloaded .iso

---

### Post by Lomok on 2010-12-09
Thanks for your advice, and time to answer.
That new executable gave me the option to install as a windows app, however it didnt recognized the iso that i downloaded.

I tricked the installer to copy from the virtual dvd by  mounting the iso after the first screen (the one where i set the user, drive, and distro).

But almost at 99% it failed. Showed me some weird error, and pointed me to the log.

Here is the log:

```
12-09 15:31 INFO   Distro: Found a valid CD for Kubuntu: H:\
12-09 15:31 DEBUG  TaskList: New task copy_file
12-09 15:31 DEBUG  TaskList: ### Running copy_file...
12-09 15:35 DEBUG  TaskList: ### Finished copy_file
12-09 15:35 DEBUG  TaskList: New task check_iso
12-09 15:35 DEBUG  TaskList: ### Running check_iso...
12-09 15:35 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
12-09 15:35 DEBUG  Distro:   checking Kubuntu ISO D:\ubuntu\install\installation.iso
12-09 15:35 DEBUG  Distro:     wrong size: 3922956288 > 900000000
12-09 15:35 DEBUG  TaskList: ### Finished check_iso
12-09 15:35 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 470, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
12-09 15:35 DEBUG  TaskList: # Cancelling tasklist
12-09 15:35 DEBUG  TaskList: # Finished tasklist
12-09 15:35 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 470, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
```

I guess the wubi intaller doesnt get along well with the DVD iso. 
I'll download the cd one, and see how it works.

Thanks

---

### Post by Lomok on 2010-12-09
UPDATE:

I've installed Kubuntu succesfully from the wubi installer, i just let it download a new iso and everything went just fine.

Weird that it didnt want to use the DVD iso.

Thanks

---

