---
title: "Windows 10 + Ubuntu dual installation, help with partitions"
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by ilipapast on 2016-11-26
So I have Windows 10 on my laptop and I want to install Ubuntu. When Ubuntu guide loads it doesn't give me an option to have a dual boot so I have to specify the partitions myself.

I'm asking you here, because I don't want to mess up anything :) 

I attach you the screenshots of my partitions so far. I don't know why I'm having 2 loaders(7 and 10) but the partition where it says windows 7 loader is my C: Drive on Windows.
[ATTACH=CONFIG]272401[/ATTACH][ATTACH=CONFIG]272402[/ATTACH]
What should I do?

THanks

---

### Post by oldfred on 2016-11-26
It looks like you have the old MBR(msdos) 4 primary partition limit.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360) 

If Windows 10 you also need to make sure fast start up is off. And Windows updates may turn it on without really telling you. And if it is turned on grub will not boot your Windows. You then need your Windows repair flash drive to temporarily install the Windows boot loader to turn it off and then reinstall grub2's boot loader.

        
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options

[/URL]
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 


[URL="http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options"]
[/URL]

---

