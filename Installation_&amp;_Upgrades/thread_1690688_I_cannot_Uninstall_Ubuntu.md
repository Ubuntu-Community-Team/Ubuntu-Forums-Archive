---
title: "I cannot Uninstall Ubuntu"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by paco42994 on 2011-02-18
Hi, I am trying to uninstall Ubuntu because I don't really use it anymore and I'm losing space on my computer.  I used Wubi to install it and it's gone through quite a few updates, so I don't know if that's why I'm having trouble.  I see there is a disks file under "C:/Ubuntu" but I don't want to mess around with things and end up permanently damaging my computer.  I checked the log file given at the error and this is what I see.


```
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {4b66b9ab-14ba-11de-992b-001f1652763c} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
```

I zipped and uploaded the log file if it helps anyone, and, since it hasn't been uninstalled, I can do the same thing with any file in Windows or Ubuntu.

I honestly wouldn't mind deleting a file if it means having to select "Windows Vista" every time I boot my computer (I'm used to it), but like I said, I don't want to kill my computer.  So, is it okay for me to delete that file if there are no suggestions?  *Are* there any suggestions?  :confused:

---

### Post by paco42994 on 2011-02-18
I did some experimenting and I found out that the ID for the boot store that the Wubi uninstaller is trying to uninstall is off by 1 letter for some reason.  Somewhere, in the middle of the ID, a B is supposed to be an A.  Is there any way I can change what it's trying to uninstall, then?  I have a feeling it wants to do more but won't because it can't do that one thing.

(The log file says the ID is {4b66b9a**b**-14ba-11de-992b-001f1652763c}.  bcdedit.exe says the ID is {4b66b9a**a**-14ba-11de-992b-001f1652763c}.)

---

### Post by paco42994 on 2011-02-18
Oh.  I figured it out.

[https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe")

Thanks everyone for all your help ;)

---

