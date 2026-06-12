---
title: "Unable to Boot Windows 8 After Install"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by amzulkifli on 2015-01-06
Hi,

I just installed Ubuntu 14.04 on a ThinkPad Edge E440. I have read this forums and others, trying the fixes suggested but none worked for me.

This is my information fron boot repair.

[http://paste.ubuntu.com/9684013/](http://paste.ubuntu.com/9684013/)

Would appreciate any help,

---

### Post by Gordonbp531 on 2015-01-06
I suspect this is a generic problem with Lenovos.
I have a Lenovo U410 that dual-boots Ubuntu and Windows 8.1 and the GRUB entry for Windows doesn't work either, and I've also tried all the fixes.
The only way I get into Windows (which I don't do very often) is with the machine powered off, to press the Lenovo Button, go into the Boot menu and choose "Windows Boot Loader.

---

### Post by oldfred on 2015-01-06
Windows has essential boot info in the NTFS partition boot sector or PBR. You overwrote that when you installed grub to the Windows partition. We have asked for years that you should not even be able to do that.

```
 sda3: __________________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda3 
                       and looks at sector 838322488 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos3)/boot/grub. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr


```

NTFS partition have a backup of the PBR, and usually you can just use testdisk to restore it. Otherwise you need a Windows repairCD or flash drive.
       Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

    
You also have wubi still installed in your Windows & it should be removed. If you have any old data recovery that first.

Also you 4TB drive has an unusual 4k/4k configuration when 512/4k is standard. But it looks like you have MBR not gpt. You should be using gpt. It this some sort of proprietary drive configuration?

 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

You also are using SFS or dynamic partitioning. That is proprietary to Windows and does not work with Linux. It used to be that you could not even install Ubuntu if SFS was seen.
       [http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

