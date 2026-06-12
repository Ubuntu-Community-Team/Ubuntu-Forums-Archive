---
title: "Volume shrink problem"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by skanimal on 2012-09-07
Hi. I was trying create a new partition to dual boot ubuntu with windows 7 64 bit. My hdd is 1tb and i have 751GB free. when i go to shrink the volume i get a small available for shrink amount.

Total size before shrink in MB      : 939430
Size of available shrink space in MB: 739

How can i be able to increase the space available to shrink?

---

### Post by oldfred on 2012-09-07
Welcome to the forums.

We always recommend shrinking with Windows tools as you are doing as sometimes using the installer or gparted Windows has issues. Even after its own shrink it will run chkdsk on a reboot, which you also need to do before installing. Use gparted or the installer to create new partitions, not Windows as it may convert to dynamic which does not work with Linux.

This was for Vista but may also apply to 7.
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by pgmer6809 on 2012-09-07
> **skanimal said:**
> Hi. I was trying create a new partition to dual boot ubuntu with windows 7 64 bit. My hdd is 1tb and i have 751GB free. when i go to shrink the volume i get a small available for shrink amount.

Total size before shrink in MB      : 939430
Size of available shrink space in MB: 739

How can i be able to increase the space available to shrink?

I can see from your JPEG that you ARE trying to shrink with windows, so the previous reply is not very helpful.

  i Believe that your problem is that there is an 'unmoveable' file on your NTFS partition.
If there is such a file, Windows will NOT move it and will NOT shrink the partition past the unmoveable file. 

I had the same experience myself.  I could not find any way around it, sorry. I tried several third party disk defragmenters and the like, and they all refused to move the 'unmovable' file to somewhere closer to the front of the disk.
The solution in my case was to re-install windows7, but that may not work for you. 
If you can reinstall win7, then shrink the partition IMMEDIATELY, before you create any system restore points, or add drivers, or do anything at all. 
(IIRC even a vanilla directory in NTFS is 'non moveable' but I am not sure about that.
There are tools you can run that will tell you what the reason for not shrinking the partition is; typically they will tell you that in cluster xxxxx  there is an unmoveable file named <aaaaaaaa> etc. But I did not find this of much help.
pgmer6809

---

