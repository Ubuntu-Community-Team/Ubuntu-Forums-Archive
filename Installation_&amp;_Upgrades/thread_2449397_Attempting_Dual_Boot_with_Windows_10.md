---
title: "Attempting Dual Boot with Windows 10"
date: 2020-08-26
forum: Installation &amp; Upgrades
---

### Post by antheah on 2020-08-26
I have an old HP G72 LAPTOP that I have upgraded successfully to Windows 10.  It is running well so I have no issues with it.

The issue that I am having, is that I have created a USB boot using Rufus, but I am unable to complete the Ubuntu install after I choose "something else".  The partitions that it pulls up, do not show the Ubuntu partition that I created using Windows Disk Management.

I tried to shrink and create a new partition but the dialog box that pops up indicates that it will format my entire disk, and I am trying to avoid that.  I will run the install once more, then post the resulting screenshots once I figure out how to do that.

"No root file system is defined.  Please correct this from the Partitioning menu"

---

### Post by Impavidus on 2020-08-26
Windows can't create a partition suited for Ubuntu. It can only create partitions with a Windows filesystem. You can use the Ubuntu live disk to format it to something useful for Ubuntu, but it's easiest to use Windows to shrink the Windows partitions, then use Ubuntu to create Linux partitions.

Without knowing what's going on exactly, I can only guess. If Ubuntu doesn't show the partitions shown in Windows, it may be that you have dynamic partitions. Those are a partitioning layer on top of the ordinary partitions and Linux doesn't understand Windows-style dynamic partitions.

You can add screenshots as an attachment to your post.

Other information that may be useful:
Is your computer booting in UEFI-style (Windows 8 or newer) or legacy-style (typical up to Windows 7, including systems upgraded from Windows 7)?
Have you disabled FastStartup? With FastStartup on, Ubuntu cannot read (although it will see) the Windows partitions. This means that the Linux boot loader will be unable to boot Windows, which can be a real problem if booting legacy style. And Windows has a habit of automatically turning FastStartup back on.

---

### Post by antheah on 2020-08-26
Aha!  It's dynamic, so how do I handle that?  Delete the current 15gb window partition, then leave it unallocated?

I inserted screenshots in my original post.

---

### Post by Impavidus on 2020-08-26
You have to convert the drive to basic partitions. It's a Windows problem, so I don't know too much about it. I read that there's no official way to convert dynamic partitions back to basic (although Windows is very eager to convert from basic to dynamic); official standpoint is that you freshly install Windows. But I also read that there are third-party tools that can do the job.

I'm guessing a bit more now. Maybe you use a hard drive that uses the old-fashioned MBR-style partition table. That's typical on older Windows systems in bios mode. In that case there's a limit of 4 primary partitions. One of those primary partitions can be an extended partition, containing as many logical partition as you like. However, when you've got 4 primary partitions and you ask Windows partition manager to create a new one, it doesn't convert to extended+logical, but it will convert all to dynamic partitions and Linux can't use that. It's not so clever of Windows, but then, Windows always assumes there's nothing else on the computer.

(Didn't see your screenshots. I'll have a look.)

gparted sees some ntfs partitions with filesystems not spanning the entire partition and too small to store an entire Windows system. It appears that gparted is confused. I think it should be solved from Windows. You indeed have 4 primary partitions.

---

### Post by oldfred on 2020-08-26
Linux does now have a driver than can at lease see dynamic partitions exist. Before you just had failure to read drive.


[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)

Other options also Aomei or even testdisk if only 4 dynamic partitions:
[http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)


But then you still have the 4 primary partition limit.
Windows uses dynamic as a way around that limit. But most use primary, extended & logical paritions. You have to convert one primary to an extended partition and then that works as a container for all the logical partitions. Windows only boots from primary partitions, but Linux boots just fine from logical partitions.

Windows 10 also makes it a bit more of a hassle to dual boot with only one drive on MBR drives. You can only boot from the one MBR and need grub to dual boot. But grub only boots working Windows and Windows 10 turns on fast start up/hibernation which then prevents grub from booting it. So you temporarily have to restore a Windows boot loader, repair Windows, & restore grub. 
Always have a Windows repair flash drive and current version of Ubuntu live installer to make repairs.

---

