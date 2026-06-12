---
title: "wubi and multiple windows installs"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by zetadin on 2010-10-01
Posting this here because I didn't see a bug reports section on the wubi website.


I'm trying to use wubi to install Ubuntu 10.04 under from Vista. I had Vista installed first and then installed W7 in another partition. Looks like my windows boot manager is on the W7 partition now. So when wubi lanches bcdedit.exe I get this error:

 > 10-01 17:58 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 628, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.



I know I could simply install it from under W7 (haven't tried yet), but for the sake of fixing bugs is there a simpler solution than getting the source, forcing bcdedit.exe to try finding the boot manager on all the NTFS partitions and then recompiling everything back into a package? (Mostly I don't want to do that because I don't know how to package the wubi.exe/lib and stuff back into the executable)


Zetadin

---

### Post by Mark Phelps on 2010-10-02
I would seriously doubt that your bootmgr is in the Win7 partition, that is, unless you manually moved it yourself.

When you install Win7 AFTER any other Windows OS, it looks for the boot partition for THAT OS and adds its boot loader files there.

To confirm this, look in each of your Vista and Win7 OS partitions for a hidden boot folder and for the bootmgr program.  My guess is that you'll find these in the Vista partition.

---

