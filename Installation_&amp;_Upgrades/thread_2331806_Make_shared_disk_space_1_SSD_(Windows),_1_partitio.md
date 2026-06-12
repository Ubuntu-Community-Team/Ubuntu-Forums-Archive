---
title: "Make shared disk space: 1 SSD (Windows), 1 partitioned HDD (Ubuntu)."
date: 2016-07-25
forum: Installation &amp; Upgrades
---

### Post by arcofark on 2016-07-25
I have a SSD with WIndows 10 installed, and I recently installed Ubuntu on a partitioned HDD.
The HDD is partitioned into two, one with Ubuntu, and the other I want to turn it into storage for both operating systems.

Right now, I can only access it from Windows 10. How can I make it so that I can access it from both operating systems?

Additionally, I currently see the SSD in the Ubuntu Files Explorer ("249 GB Volume"). Is there a way to make it so that I can't see this?

---

### Post by oldfred on 2016-07-25
Windows fast startup is always on hibernation. And it leaves all NTFS partitions in that hibernated state. 
Linux driver will not then mount (see) the NTFS data partition.

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 

You should not normally write into the Windows system partition.
And either to make it read-only or not seen you actually have to mount it to hide it.

      
 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Standard mount for your data partition:
       
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 
    
Some examples of different fstab entries to mount read only or hidden.

 # Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

---

### Post by oldfred on 2016-07-25
Windows fast startup is always on hibernation. And it leaves all NTFS partitions in that hibernated state. 
Linux driver will not then mount (see) the NTFS data partition.

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 

You should not normally write into the Windows system partition.
And either to make it read-only or not seen you actually have to mount it to hide it.

      
 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Standard mount for your data partition:
       
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 
    
Some examples of different fstab entries to mount read only or hidden.

 # Hide mount template examples with noauto,  you have to make the mount points yourself first
sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all, UUID is better than this example with device mount
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
sudo mkdir /mnt/reserved
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
sudo mkdir /mnt/win7
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

---

### Post by yancek on 2016-07-25
If you can access it from windows then it must be either FAT32 or ntfs as windows by default can't read Linux filesystems.  What have you tried to access the partition?  Partitions other than the system partition are usually available under the /media/user directory (substitute your user name) as a UUID.  Have you looked there.  Do you have ntfs-3g installed?  It is necessary to read windows ntfs filesystems.

---

### Post by arcofark on 2016-08-06
Hi oldfred, yancek

Thank you for the help again. I have got it working very nicely.

---

