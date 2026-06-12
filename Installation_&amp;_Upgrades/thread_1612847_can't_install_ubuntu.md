---
title: "can't install ubuntu"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by tortug45 on 2010-11-03
Hi everyone,


I'm trying to install ubuntu 10.10 in my laptop; toshiba satelite L635 intel core i5. When trying to install from windows using wubi it returns the following error:
```

**************
 11-03 12:33 ERROR  TaskList: [Errno 13] Permission denied
> Traceback (most recent call last):
>    File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
>    File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
> IOError: [Errno 13] Permission denied
> 11-03 12:33 DEBUG  TaskList: # Cancelling tasklist
> 11-03 12:33 DEBUG  TaskList: New task check_iso
> 11-03 12:33 ERROR  root: [Errno 13] Permission denied
> Traceback (most recent call last):
>    File "\lib\wubi\application.py", line 56, in run
>    File "\lib\wubi\application.py", line 128, in select_task
>    File "\lib\wubi\application.py", line 194, in run_cd_menu
>    File "\lib\wubi\application.py", line 118, in select_task
>    File "\lib\wubi\application.py", line 156, in run_installer
>    File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
>    File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
> IOError: [Errno 13] Permission denied
> 11-03 12:33 DEBUG  CommonBackend: Searching for local ISO
> 11-03 12:33 DEBUG  CommonBackend: Could not find any ISO or CD,
> downloading one now
> 11-03 12:33 DEBUG  TaskList: New task get_metalink
> 11-03 12:33 ERROR  TaskList: Cannot download the metalink and therefore
> the ISO
> Traceback (most recent call last):
>    File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
>    File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
>    File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
> Exception: Cannot download the metalink and therefore the ISO
> 11-03 12:33 DEBUG  TaskList: # Cancelling tasklist
> 11-03 12:33 DEBUG  TaskList: # Finished tasklist
>
> ************************************

```
I thought it was a graffic card recognition problem so I tried to install it booting from the cd and giving it the option vga=711 or even trying different configurations but none worked. I know the disk isn't broken or hasn't corrupt files because I've used it in another computer without problems. 

thanks

tortug45

---

### Post by bcbc on 2010-11-03
Generally, run wubi.exe as an administrator (Right click, Run as Administrator). Allow pyrun.exe access to the firewall. Make sure you're connected to the net.

Despite doing the above, some people still get the same error and I am not sure what causes it. (It's a python error - which wubi is written in).

The workaround (if you've done everything else right) is to download the ubuntu install image (.iso file) yourself. Place it in the same folder as wubi.exe, and run wubi.exe from there.

---

