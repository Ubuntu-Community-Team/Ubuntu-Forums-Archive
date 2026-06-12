---
title: "Trying To install Ubuntu Next To windows 10"
date: 2018-01-30
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2018-01-30
I have a Dell Inspirion 3000 and it has Windows 10 on a 2 TB hard drive.  I've gone in Windows and created to separate 1 TB partitions.  I've installed Ubuntu 16.04.2 on a 8 GB flash drive and boot to it.  I start the installation and I usually get to the screen that says install Ubuntu next to Windows, but I do not see it on this install.  So I select Something Else, but do not see the 2 1 TB partitions.  What could I be doing wrong?

---

### Post by ubfan1 on 2018-01-31
These have to be basic partritions (not dynamic partitions).  Then the recommended installation method is to just free up the space, and let the  Ubuntu installer create partitions is needs (root, swap, home,... etc.).

---

### Post by yancek on 2018-01-31
I would suggest that you thoroughly read through the Ubuntu documentation below on dual booting with windows 10 if it is UEFI before beginning.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-01-31
Make sure Windows fast start up is off.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) 

Also since Windows updates will turn fast start up back on, be sure to have a Windows repair/recovery disk and good backups of your Windows install.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media

[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]
[/URL]

---

### Post by shane_faulkinbury2 on 2018-01-31
Thanks guys on all the recomendations, but I think oldfred got it!  I forgot to turn Fastboot off!!!  :D

---

### Post by shane_faulkinbury2 on 2018-02-03
Thanks OldFred, it's seems like all it took was shutting that Fast Startup off!  All is loaded and running smoothly!  Thanks again

---

### Post by oldfred on 2018-02-03
Glad you got it working. :)

---

