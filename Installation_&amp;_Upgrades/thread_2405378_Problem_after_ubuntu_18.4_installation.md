---
title: "Problem after ubuntu 18.4 installation"
date: 2018-11-05
forum: Installation &amp; Upgrades
---

### Post by reikidude89 on 2018-11-05
Hi

I have installed ubuntu near windows 10, but after that i can't be able to boot with neither.

I've tried to use boot repar, from an usb-live ( i've followed this guide [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ), i have also removed the secure-boot and set the uefi mode, but it still not work.

Boot-repair give me this  log error

[http://paste.ubuntu.com/p/Ffh947Mvhg/](http://paste.ubuntu.com/p/Ffh947Mvhg/)

Can you help me?

Thank you

---

### Post by oldfred on 2018-11-05
Microsoft has dynamic partitions. It is proprietary to Microsoft & does not work with Linux. But its main purpose was a work around for the old MBR limit of 4 primary partitions.
But with the new gpt partitioning used with UEFI, there is no real limit on partitions (its 128, but can be user changed).

But for some reason you have dynamic partitions with gpt partitioning.
Just to understand, how does that happen?

>     Logical Disk Manager (LDM) metadata partition (Windows) 



Many with old BIOS/MBR configurations have done it and Microsoft does not have an undo. It recommendation is full backup, erase drive, and reinstall.
But with MBR there are several third party tools that have worked. But good backups still required, just in case.
But have not seen many gpt dynamic partition configurations and do not know if or how well third party tools work.

       You may be able to see dynamic partitions from Linux:
sudo apt-get install ldmtool 

      
 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[URL="https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv"]https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv

      [/URL]
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html) 
    [URL="https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv"]
[/URL]

---

