---
title: "Error: There is no disk in the drive. Please insert a disk into drive"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by dconrad on 2011-10-14
I just downloaded and installed Ubuntu with Wubi. When I ran Wubi I got the following error message:

There is no disk in the drive. Please insert a disk into drive
\Device\Harddisk1\DR1.

                Cancel        Try Again        Continue

[IMG]http://img692.imageshack.us/img692/5408/wubi.png[/IMG]

I tried clicking all three buttons, but the error (from pyrun.exe) popped up over and over again. Even killing it from the Windows Task Manager didn't work, at first, although after several tries it finally went away.

I tried running Wubi a second time, and this time, after bypassing the error message a dozen or more times (clicking Continue), the installer finally ran. Then I got the error a few more times while it was installing. Finally it completed, rebooted, and the install completed successfully.

Any idea what is going on, here?

Details on the copy of wubi.exe I downloaded (this morning): 

dconrad@darwin ~/dl
$ ls -l wubi.exe
-rwx------+ 1 dconrad None 2493512 Oct 14  2011 wubi.exe

dconrad@darwin ~/dl
$ sha1sum wubi.exe
379dca65aba85a73bd6f57911044ab9bd53b5a55 *wubi.exe

Regards,
David

---

