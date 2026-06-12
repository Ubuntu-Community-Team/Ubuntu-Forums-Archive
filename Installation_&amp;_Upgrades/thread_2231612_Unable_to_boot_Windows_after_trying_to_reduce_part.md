---
title: "Unable to boot Windows after trying to reduce partition size"
date: 2014-06-26
forum: Installation &amp; Upgrades
---

### Post by Daksh_Shah on 2014-06-26
I loaded up the latest Ubuntu 14.10 on my USB drive and booted using it.
As my aim was to install Ubuntu alongside my already existing Windows 8.1 installation, I went to GParted Partition Editor in order to reduce the size of my Windows partition as there was plenty of free space (200GB+) available on that partition. While the process was going on, it suddenly hangs up and my laptop shuts down.

And the next thing I know, I get a Windows blue screen error telling me that a device is disconnected and it cannot boot. It now gets stuck in boot cycles repeatedly.

After using Boot Repair from my live Ubuntu USB, I got the following URL: [http://paste.ubuntu.com/7707702](http://paste.ubuntu.com/7707702)
Now, I get a 'Operating System Not Found' error when I try to boot.

And yes, I confirmed that my Windows parititon still exists. I can still see all of my files from within Ubuntu on my Windows partition. The only probelm is that Windows isn't booting up.
Here's a screenshot of that: 

[ATTACH=CONFIG]254263[/ATTACH]

I hope the many professionals and enthusiasts can help me boot into Windows again. Thanks a lot :)

---

### Post by yancek on 2014-06-26
Ubuntu 14.10 is still in testing stage and not ready for release.  You are also usually better off re-sizing a windows partition with windows software.
The info you posted shows you do not have Grub or windows bootloader info in the master boot record but rather, syslinux.  Did you intend to do that?
You have 2 windows partitions and 3 unknown filesystem partitions.

If you want to boot windows you will need either a full installation disk or a recovery disk you created when your first booted the computer.  Select the Repair option.  There are probably other tools you can use but I'm not that familiar with windows.

---

### Post by ajgreeny on 2014-06-26
Oh dear!!

You should _**always**_ change windows partitions using windows own disk management software, never with Linux software. Even if you had not had the shutdown when you were using gparted, you may still have had a problem booting Win8.

I have no idea if boot-repair will be successful for you in this situation and suggest you wait a bit longer for other forum users to post replies.  However, I wonder if you made sure that Win8 was completely powered off, ie a full shutdown, not the default hibernated state that it uses, which can cause big problems for dual boot systems if not managed properly.

---

### Post by LastDino on 2014-06-26
Not the solution but note for future: Never try to resize windows partition using anything other than partition tool in windows itself.

As for getting it fixed, 
```

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 28481536. But according to the info from 
                       fdisk, sda1 starts at sector 63. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda1 has 
                       204799 sectors, but according to the info from fdisk, 
                       it has 1984 sectors.
```
Probably gives you a hint, fixing this would probably require rebuilding BCD.

---

### Post by oldfred on 2014-06-27
You have another major issue.
You created partitions with Windows partition tools and it converts to dynamic partitions (shown as SFS in fdisk). Linux cannot use SFS partitions as that is proprietary to Microsoft. 

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

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

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

