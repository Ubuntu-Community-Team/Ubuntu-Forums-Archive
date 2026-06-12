---
title: "Ubuntu can not mount win10 partition"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by alcapone-g on 2016-09-26
I upgraded Ubuntu from 14.04 t0 16.04 and the last upgrade does not mount my win10 partition. I get message that win10 partition has errors or was hibernated and that makes mounting failure in ubuntu 16.04. I did check partition on win10 and it does not have an error and win 10 was shout down not hibernated. I did not have any problem with mounting this win 10 partition on ubuntu 14.04.before upgrade. does anybody knows fix for it?

---

### Post by oldfred on 2016-09-26
Run chkdsk in Windows until no errors. And make sure fast start up or always on hibernation is off.

The Linux NTFS driver will not mount NTFS that is hibernated, nor if it needs chkdsk to prevent damage that chkdsk may not then be able to fix.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html
[/URL]
 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 

      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]
[/URL]

---

