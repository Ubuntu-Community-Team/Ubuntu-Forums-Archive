---
title: "Problem reinstalling wubi under Windows7"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by sza on 2010-05-17
Hi all,
I've installed Ubuntu 9.04 wubi installation under windows 7 and somehow it's stopped working all of the sudden. (can't log in threw BCD boot menu it's just disappeared. I think that happent because my brother played with it. he downloaded a program named EasyBCD and changed things...)

I didn't know how to log the ubuntu installation and saw the new ubuntu 10 so I downloaded it and tried to uninstall the old wubi version in order of installing the new version.

While the uninstallation was running there was an error:

```

05-17 15:33 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {4d230aa4-1120-11df-bd59-a4090843b74e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 499, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 682, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {4d230aa4-1120-11df-bd59-a4090843b74e} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=

```

The wubi installation is still written as installed on my computer... and the new wubi installation can't start until the last will disappear from that list...

Can you please help me?

Thanx a lot!

---

### Post by sza on 2010-05-24
Please... can anyone help? :(
I still didn't find any solution and don't want to format my entire H.D

---

### Post by bsm1th on 2010-06-06
Same problem I am having. What the uninstall is trying to do and failing at is removing (the nonexistent) BCD entry for ubuntu. BCD uses a checksum made from the name used. We both need the exact name that install puts into the BCD menu. Hopefully, with that name, we can make a fake entry with EasyBCD so the uninstall will have something to chew on. That SHOULD cause the uninstall to end correctly. That way another install will work.

Bob <bsm2th@gmail.com>  :mad:

---

