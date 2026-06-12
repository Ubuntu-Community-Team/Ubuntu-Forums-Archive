---
title: "error in upgrade to 12.04 (64 bit) from 11.10 (64 bit) using wubi as installer"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2013-01-18
I was having Ubuntu 11.10 , the upgrade to 12.04 caused problems , so
I decided to reinstall,
the original was installed using Wubi I do not have an extra partition
to install in a separate one
so that I could use Unetbootin and 12.04 ISO so I decided to go the
Wubi way however when ever
I double click wubi I get error and it says previous install needs to
be uninstalled I click next but I get
lots of errors I have pasted the errors here
[http://paste.ubuntu.com/1545678/](http://paste.ubuntu.com/1545678/)
```

     'en']
        01-18 20:26 DEBUG  TaskList: # Running tasklist...
        01-18 20:26 DEBUG  TaskList: ## Running Remove bootloader entry...
        01-18 20:26 DEBUG  WindowsBackend: Removing bcd entry
{913c60b1-d90e-11e0-9e01-869473ab8036}
        01-18 20:26 ERROR  TaskList: Error executing command
        >>command=C:\Windows\sysnative\bcdedit.exe /delete
{913c60b1-d90e-11e0-9e01-869473ab8036} /f
        >>retval=1
        >>stderr=An error occurred while attempting to delete the
specified entry.

        The system cannot find the file specified.


        >>stdout=
        Traceback (most recent call last):
          File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
          File "\lib\wubi\backends\win32\backend.py", line 562, in
undo_bootloader
          File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
          File "\lib\wubi\backends\common\utils.py", line 66, in run_command
        Exception: Error executing command
        >>command=C:\Windows\sysnative\bcdedit.exe /delete
{913c60b1-d90e-11e0-9e01-869473ab8036} /f
        >>retval=1
        >>stderr=An error occurred while attempting to delete the
specified entry.

        The system cannot find the file specified.


        >>stdout=
        01-18 20:26 DEBUG  TaskList: # Cancelling tasklist
        01-18 20:26 DEBUG  TaskList: # Finished tasklist
        01-18 20:26 ERROR  root: Error executing command
        >>command=C:\Windows\sysnative\bcdedit.exe /delete
{913c60b1-d90e-11e0-9e01-869473ab8036} /f
        >>retval=1
        >>stderr=An error occurred while attempting to delete the
specified entry.

        The system cannot find the file specified.


        >>stdout=
        Traceback (most recent call last):
          File "\lib\wubi\application.py", line 58, in run
          File "\lib\wubi\application.py", line 132, in select_task
          File "\lib\wubi\application.py", line 145, in run_installer
          File "\lib\wubi\application.py", line 181, in run_uninstaller
          File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
          File "\lib\wubi\backends\win32\backend.py", line 562, in
undo_bootloader
          File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
          File "\lib\wubi\backends\common\utils.py", line 66, in run_command
        Exception: Error executing command
        >>command=C:\Windows\sysnative\bcdedit.exe /delete
{913c60b1-d90e-11e0-9e01-869473ab8036} /f
        >>retval=1
        >>stderr=An error occurred while attempting to delete the
specified entry.

        The system cannot find the file specified.


        >>stdout=

```

lots of errors I have pasted the errors here
[http://paste.ubuntu.com/1545678/](http://paste.ubuntu.com/1545678/)

How to install 12.04 using Wubi when already 11.10 is existing and
that too was installed using 11.10 I want to remove 11.10.
The upgrades by all known methods do-release-upgrade after final
finish gave me a black screen.

how ever it appears the ability to install using wubi has been disabled as mentioned on this message
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-March/034970.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-March/034970.html)

please let me know if there is a situation for people like me on Windows 7.
I do not have spare Windows partition to be able to give it to Ubuntu so I am preferring Wubi if there is any other way let me know.

---

### Post by Mark Phelps on 2013-01-20
Wubi was never designed to be a long-term solution, such that it could be upgraded from release to release.

If you really want to keep what you've got and upgrade it to 12.04. a better solution would be to do the following:
1) Migrate the Wubi install to its own partition OUTSIDE of the Windows partition
2) Upgrade THAT install to 12.02.

For migration instructions, see the link below:

[http://ubuntuforums.org/showthread.php?t=1519354]("http://ubuntuforums.org/showthread.php?t=1519354")

---

