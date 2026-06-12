---
title: "Problem booting Windows 7 paralel installation with Ubuntu"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by arisk on 2012-04-23
Hi

I have problem booting Windows 7. Here is report from boot-repair:

[http://paste.ubuntu.com/942365/](http://paste.ubuntu.com/942365/)

I appreciate your help.

Best regards
A.

---

### Post by darkod on 2012-04-23
SFS type for the windows partition means the disk is dynamic in windows. Usually it wouldn't even allow to install ubuntu if the disk is dynamic.

SFS is a Microsoft format that ubuntu can't fully read and that's why it can't boot win7 from SFS.

If you want to, you can consider converting the disk to Basic but I can't recommend any tools for that since I don't use dynamic disks. Google search will help you in that.

---

### Post by oldfred on 2012-04-23
some more info:

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

---

### Post by YannBuntu on 2012-04-24
**@arisk:** when you clicked the "Recommended repair" button, Boot-Repair should have displayed the following message:
> SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as MiniTool Partition Wizard or EASEUS Partition Master. Do you want to continue?


Did you see this message? (just to check it works correctly)

---

### Post by Conco on 2012-11-20
@^

I got that message... but i've been trying to install something in Ubuntu to convert it from dynamic to basic but I dont find any program or tool... What should I do ?

---

### Post by YannBuntu on 2012-11-20
> **Conco said:**
> i've been trying to install something in Ubuntu to convert it from dynamic to basic but I dont find any program or tool... 

I think TestDisk can do it.

OR, recover direct access to Windows this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , then use MiniTool Partition Wizard or EASEUS Partition Master from Windows.

---

