---
title: "Can't boot to Windows 8"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by Daniel_Billing on 2013-09-09
[http://paste.ubuntu.com/6083828/](http://paste.ubuntu.com/6083828/)
[http://paste.ubuntu.com/6083664/](http://paste.ubuntu.com/6083664/)

When i boot to Ubuntu I can see the disk in GParted. I have tried to use Boot-repair-disk but without luck. When I can choose what OS to boot I can choose "Windows UEFI bkpbootmgfw.efi" and "Windows Boot UEFI loader" but both give me this error:
"error: no such device: 92AA-E753
error: file not found."

Any suggestions?

---

### Post by ubfan1 on 2013-09-09
Make your EFI partition on sda1 bootable (set the boot flag in gparted).  That's if you're booting in UEFI mode.  If you are booting in legacy mode, why are you using syslinux instead of grub?

---

### Post by oldfred on 2013-09-09
Welcome to the forums.

You have several issues. Wubi does not work on gpt partitioned drives which sda is. And Linux does not work with dynamic partitions (shown as SFS) at all.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

You may be able to undo some of the SFS partitions if you still have a one to one logical to phyical relationship. If you have more logical than physical then you may not be able to convert back.

      
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

Ubuntu is on MBR disk and may boot from that drive by choosing it in BIOS in BIOS mode after you install grub to the MBR of that drive, but cannot boot a Windows in UEFI mode. Your Windows in sda should still boot from UEFI menu.
With Multiple drives do not use auto repair. uncheck that, check update MBR, and in advanced choose to install grub just to Ubuntu sde drive.

Better to have all drives as gpt not MBR if system is UEFI.
       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

