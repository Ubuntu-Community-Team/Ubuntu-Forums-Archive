---
title: "No boot after dd"
date: 2016-03-05
forum: Installation &amp; Upgrades
---

### Post by n-mike-3 on 2016-03-05
Hello all, I dd'd my original dual booting disk to a img file and swapped in a spiffy new ssd drive of the same size.  dd the image to the new drive but it won't boot now.  My laptop is using uefi boot.  Now I can't boot.  From what I read I most likely have a grub issue.  I can boot to live cd 14.04.  I have two questions

1.  Can someone let me know what commands I need to run in order to restore grub?  
2.  What partitions are necessary for a dual booting windows 10 and ubuntu 14.04?  This machine came with extra partitions from Lenovo for recovery and diagnostics and who knows what, I'd like to remove them.  
3.  For future reference, if I dd a disk again, is there any way to grab grub and so that when I restore it just runs?

[ATTACH=CONFIG]267658[/ATTACH]

---

### Post by sudodus on 2016-03-05
Please check that

1. The drives (source and target) are exactly the same size.

The target must not be one single byte smaller, but it can be larger. In UEFI there is usually a GUID partition table, and if the target drive is larger, you must fix the backup of the partition table at the end of the drive. You can do that with ***gdisk*** in expert mode.

2. The sector size is the same on the source and target drives.

You can check the sector size with ***gdisk*** or ***parted***.

```
sudo gdisk -l /dev/sdx  # ... space minus ell ...
sudo parted -ls
```

---

### Post by oldfred on 2016-03-05
Generally dd is not the best tool for gpt(GUID) partitioned drives. Plus dd copies all space so much slower copy process. 
And you must copy entire drive exact size to size as sudodus mentions above as partitions have GUID & partition tables have GUIDs that must match.

If UEFI, then the files in the ESP - efi system partition are all that is required.

But I believe Windows requires an image copy, but do not know best tools for Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media) 
    
I normally suggest just re-installing Ubuntu and copy /home and/or all other data into new install with rsync or cp -a commands.

---

