---
title: "wubildr not found during install"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by frankendong on 2012-03-21
well,
 
i have an hp mdeia center desktop running xp, it has multiple flash drives that seem to be a problem for wubi during the last part of the install.
 
looks like it is trying to install wubildr on all available and unavailable flash media drives...and not just the target hard drive.
 
i have tried several times on 2 different hard drives and the results are the same...
 
when looking at the install log file you can see that it is looking for wubildr on the G: drive...which is a removeable media drive...
 
here is a sample of the log:
 
03-19 08:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\HP_ADM~1\LOCALS~1\Temp\pyl27.tmp\winboot -> F:\ubuntu\winboot
03-19 08:31 ERROR TaskList: [Errno 2] No such file or directory: 'G:\\wubildr'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'G:\\wubildr'
03-19 08:31 DEBUG TaskList: # Cancelling tasklist
03-19 08:31 DEBUG TaskList: # Finished tasklist
03-19 08:31 ERROR root: [Errno 2] No such file or directory: 'G:\\wubildr'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 58, in run
File "\lib\wubi\application.py", line 132, in select_task
File "\lib\wubi\application.py", line 158, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'G:\\wubildr'
 
anyone?
 
thx mucho

---

### Post by Frogs Hair on 2012-03-21
Hello and Welcome 

See this Thread.[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

### Post by bcbc on 2012-03-21
That's bug [lpbug]862003[/lpbug]. The install is successful, reboot to complete.

---

