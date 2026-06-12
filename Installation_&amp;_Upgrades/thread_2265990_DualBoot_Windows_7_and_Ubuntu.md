---
title: "DualBoot Windows 7 and Ubuntu"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by anders13 on 2015-02-19
Hello,

I have installed Ubuntu after installing Windows 7. Now when i boot I can only choose Ubuntu i GRUB. It shows windows 7 as a possibility but I get an error when entering Windows. Before GRUB is showed I get the error "Invalid Partition Table!".
The error message from Boot-Repair is:
[http://paste.ubuntu.com/10303780](http://paste.ubuntu.com/10303780).

I have tried updating grub and boot-repair but nothing helped. Can someone please help since i have no idea what to do.

Best Regards
Anders

---

### Post by oldfred on 2015-02-19
Fdisk is showing  sdb as SFS which is Windows dynamic partitioning. It is somewhat like LVM in Linux as a way around the 4 primary partition limit in MBR(msdos) partitioning. But it is proprietary to Windows and will not work with Linux. Best to remove the dynamic partitions.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)


 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

