---
title: "Usual ntfs partitions automatically mounted as read-only since not long"
date: 2017-01-01
forum: Installation &amp; Upgrades
---

### Post by HerixFromParis on 2017-01-01
(SeansonsGreating.jpg)

Dual boot with two disks, four main partitions, two of which ntfs.
The ntfs partitions automagically appear on my desktop, which is nice. Until recently, just double-clicking on the corresponding icon would open them in read-write mode, which was nice. Long story, I made a fresh instal of everything. Xubuntu is now 16.10 and Windows version 10, which is also nice.
Still have the ntfs icons, but now they stubornly open them in read-only mode, which is *not* nice.


I suppose I could mount them manually, although it's been some time since I last did that and I would need a bit of thinking.
Right now, said partitions are *not* listed in ```
fstab
```. I suppose I could add them there, but for reasons, I'd rather not.
When installing, I may or may not have omitted to install some anciliary package like ```
ntfs-3g
``` but my previous configuration was the result of continuous upgrades since times imemorial so I've forgotten where to start looking.

Hence questions :


* Why is that ? Is it something new with 16.10 ?
* How can I reinstate the previous behaviour, to wit double-click => auto-mount r/w ?

cheers + thanks

---

### Post by wildmanne39 on 2017-01-01
*Thread moved to **Installation & Upgrades**.*

---

### Post by yancek on 2017-01-01
The 'ntfs-3g' software is required to write to any proprietary ntfs filesystem so I would start with installing that.

---

### Post by Impavidus on 2017-01-01
> **HerixFromParis said:**
> 
* Why is that ? Is it something new with 16.10 ?
* How can I reinstate the previous behaviour, to wit double-click => auto-mount r/w ?

I don't think it's something new with Ubuntu 16.10. I think it's something new with Windows 10. It has fast startup enabled by default, to hide the fact Windows 10 boots so slow. With fast startup enabled, Windows doesn't cleanly unmount its file systems. As a result of that Ubuntu cannot mount these ntfs partitions in read-write mode. It should be possible to disable this setting in Windows.

You may also want to make sure that ntfs-3g is installed, although I think that it's supposed to be installed by default and without it the ntfs partitions woundn't be mounted at all.

---

### Post by oldfred on 2017-01-01
Just to add to Impavidus' suggestion.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[URL="http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions"]http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions

[/URL]Be sure to create a Windows repair/recovery flash drive.
Windows on updates may turn the fast start back on. Or NTFS may need chkdsk.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by HerixFromParis on 2017-01-02
Thank you for this detailed answer, and thank everybody else for the hints. Sure enough, the culprit was Fast Boot. I disabled it in the control panel, problem solved.
I had indeed noticed that Windows started surprisingly fast, wich was nice but suspicious.

Damn Windows, acting like it owns the place and was alone in the world.

Spot on :-)

---

