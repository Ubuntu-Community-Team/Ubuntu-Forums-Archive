---
title: "Ubuntu installer doesn't recognize Windows partitions"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by Aftrumpet on 2013-05-18
Hi, I just attempted to install Ubuntu Studio alongside my existing Windows 8 installation. It is a Lenovo Y500, but after I did a clean install the disk appears to be MBR and boots in legacy mode. When I went into the installer though, there was no option to install Ubuntu alongside Windows 8, and it showed my Windows disk as being entirely unallocated space. Part of it could be due to the fact that I formatted the disk when reinstalling Windows 8, changing it from GPT to MBR. There was a 129 GB drive that showed up on the desktop that could be the Windows disk, but when I tried to click on it I got an error saying the drive could not be mounted. Below are screenshots of the Ubuntu installer and disk management:
[https://www.dropbox.com/s/b3nfw6na14oejz9/ubuntuinstallation.png](https://www.dropbox.com/s/b3nfw6na14oejz9/ubuntuinstallation.png)
[https://www.dropbox.com/s/bo8seyoe63lr5u7/diskmgmt.png](https://www.dropbox.com/s/bo8seyoe63lr5u7/diskmgmt.png)
Any steps that I should take to figure out my problem? Help would be appreciated.

---

### Post by oldfred on 2013-05-18
If drive was gpt and you reinstall Windows in BIOS/MBR mode it overwrites the primary gpt partition table. But gpt also has a backup and Windows seems to ignore it.
But Linux sees a MBR table and a backup gpt table and gets confused. You need to delete backup gpt table with fixparts.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Above may apply but I should have looked at screen shots. You converted to dynamic partitions which do not work with Linux and may not work with all Windows repair tools.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by fantab on 2013-05-18
MBR has ONLY FOUR Primary partition limit. When you force a FIFTH the disk gets converted to Dynamic... and Linux WILL NOT work with Dynamic. Your 'D' shows as Dynamic. You have get it back to BASIC: [http://www.partition-tool.com/easeus-partition-manager/convert-dynamic-disk-to-basic-disk.htm](http://www.partition-tool.com/easeus-partition-manager/convert-dynamic-disk-to-basic-disk.htm). 

Since you have converted your GPT to MBR you may have to run [FIXPARTS]("http://www.rodsbooks.com/fixparts/") to remove GPT backup Table, or it will too cause issues. I suggest you do complete re-install after fixing your partitions.

Edit: oldfred beat me to it with a more comprehensive explanation.

---

### Post by Aftrumpet on 2013-05-18
The dynamic disk is just my secondary drive which stores documents. Easy fix since not many documents are on there, but that shouldn't affect the main disk that will contain the dual operating systems. I will be sure to try FixParts and report back on the outcome.

Edit: FixParts worked and I now have a working dual boot! Will marked as solved.

---

