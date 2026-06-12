---
title: "Trying to repair Win 7 boot with boot-repair"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by maazmahmood on 2014-09-17
So I'm trying to repair the windows 7 bootloader, and I get the following error.
[http://paste.ubuntu.com/8369151/](http://paste.ubuntu.com/8369151/)

---

### Post by oldfred on 2014-09-17
You have SFS or dynamic partitions on sdb which will give all sorts of issues to Linux. Even some Windows repairs do not work with SFS so I would suggest you undo that. Microsoft makes it easy to convert to dynamic but has no undo.
       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

I so not see anything specific wrong with your install in sde2. I might use Boot-Repair to install a Windows boot loader to sde, so from BIOS you can directly boot Windows if grub give issues.

You also have several gpt partitioned drives. To correctly install grub to boot in BIOS mode from a gpt partitioned drive you also must have a bios_grub partition somewhere on the drive. It should be 1 or 2MB with the bios_grub flag.

Do not use Boot-Repairs auto-fix as that just tries to install grub to every MBR and you do not want that. And it will just give errors on every gpt partitioned drive that does not have the bios_grub partition. 
If you are later planning on moving drive to a newer computer that is UEFI, I might also include an efi partition of 300 to 500MB at beginning of drive for future efi partition. Not a lot of space to use for future compatibility. And it is very difficult to add an efi partition to beginning of drive when it has lots of data.

Boot-Repair can only make minor fixes to Windows. You in most cases need the Windows repairCD or flash drive. You make that for free if you can boot Windows, but some vendors charge up to $40 to download it later.

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $20 or $40  for the download. So make one yourself before you have to pay to get one.
[http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)
Make your own Windows recoveryCD/repair: (free)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by maazmahmood on 2014-09-19
Would I lose all my data on that dynamic partition?

---

### Post by fantab on 2014-09-19
> **oldfred said:**
> 
       **Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo**.

You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.



If you try third-party tools for conversion, you may or may not lose data... Good Backup of your data on another disk, usb, dvd, or even a cloud is recommended.

---

