---
title: "Boot loading issue"
date: 2018-11-23
forum: Installation &amp; Upgrades
---

### Post by rjgamer8 on 2018-11-23
Tried to install ubuntu 18 LTS in my windows 7 for dual booting. There was
a fatal error ignored by me about the bootloader. Please help to recover my
pc.
Here is my boot repair report :
[http://paste.ubuntu.com/p/QKMgtkKMfh]("http://www.google.com/url?q=http%3A%2F%2Fpaste.ubuntu.com%2Fp%2FQKMgtkKMfh&sa=D&sntz=1&usg=AFQjCNEqKDqfEwIyoo1zbc7ZfRH3AzmiBQ")

---

### Post by oldfred on 2018-11-23
Report shows SFS which is dynamic partitions in Windows.
It used to be that Linux would not even see a dynamic partitioned drive, but now it does.
But it will not fully work with it, and it turns out many Windows tools may not work with dynamic partitions as they are not basic partitions.
Best to undo the dynamic partitions. You may want to make sda4 the extended partition and then install Ubuntu into logical partitions.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html
      [/URL]
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html) 
    

Be sure to have good backups before any major partition change like this.[URL="http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html"]
[/URL]

---

### Post by rjgamer8 on 2018-11-25
May I just do my full backup through booting in by try ubuntu option from my bootable pendrive and erase everything else from my disk and do a full install ubuntu in my entire disk.

---

### Post by oldfred on 2018-11-25
You do not fully backup Windows from Ubuntu, normally. 
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media


[/URL]

---

