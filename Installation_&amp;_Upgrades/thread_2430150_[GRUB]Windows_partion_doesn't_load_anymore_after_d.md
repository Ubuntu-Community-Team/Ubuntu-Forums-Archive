---
title: "[GRUB]Windows partion doesn't load anymore after disk replacement"
date: 2019-10-28
forum: Installation &amp; Upgrades
---

### Post by elica on 2019-10-28
Hello all, i have a machine with two disks, 1 for Linux and 1 for windows 10. I replaced my ubuntu ssd disk with a bigger one, grub recongized it smoothly while the w10 partition no longer boot. If i press on the windows entry on grub it points to the windows recovery partition. I think that GRUB is pointing to the wrong path after the disk replacement since from fdisk i now have windows on dev/sdb3 while GRUB says it is on /dev/sdb1. How can i change the path of the entry on grub? Many thanks

---

### Post by oldfred on 2019-10-28
Windows boot is usually from first or second drive. 
With BIOS it boots from a separate small often 100MB boot partition.
With UEFI it boots from the ESP - efi system partition.
Main install then is in a later partition.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

May be best to see details of your specific configuration, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by elica on 2019-10-29
> **oldfred said:**
> Windows boot is usually from first or second drive. 
With BIOS it boots from a separate small often 100MB boot partition.
With UEFI it boots from the ESP - efi system partition.
Main install then is in a later partition.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

May be best to see details of your specific configuration, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
   

So this is the parted -l output:

```

Model: ATA CT500MX500SSD1 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot, esp
 2      538MB   500GB  500GB  ext4


Model: ATA SK hynix SC311 S (scsi)
Disk /dev/sdb: 256GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  525MB  524MB   fat32        EFI system partition          boot, esp
 2      525MB   660MB  134MB                Microsoft reserved partition  msftres
 3      660MB   241GB  241GB                Basic data partition          msftdata
 4      241GB   242GB  870MB   ntfs                                       hidden, diag
 5      242GB   255GB  12.8GB  ntfs                                       hidden, diag
 6      255GB   256GB  1236MB  ntfs                                       hidden, diag

```


And that's the link to my boot-repair summary : [http://paste.ubuntu.com/p/Zcmr73g4WV/](http://paste.ubuntu.com/p/Zcmr73g4WV/)

---

### Post by yancek on 2019-10-29
Your boot repair output shows 2 entries for windows.  The first one which has a menuentry line of:

> menuentry 'Windows Boot Manager (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-efi-3EE5-46BE' 

should be the one that works as it should point to the boot file on the EFI partition (chainloader /efi/Microsoft/Boot/bootmgfw.efi).  The windows system partition is sdb3.

Remove the windows entry from /etc/grub.d/40_custom as it points to the wrong partition then run sudo update-grub.  Also, I see the message below in several places in the boot repair output which looks problematic.  Might try running chkdsk if you can get windows to boot.  I don't really know what the problem would be as I don't use windows.

> The device '/dev/sdb3' doesn't seem to have a valid NTFS.

---

### Post by oldfred on 2019-10-29
It looks like the Windows entry in grub to boot Windows is correct. It refers to the ESP on the Windows drive.
But grub only boots working Windows, so you want to maintain a valid Windows UEFI boot entry which may let you get to the internal repair console and a Windows repair flash drive or installer with repair console.

Can you directly boot Windows from UEFI boot menu? Same key you use to boot flash drive, often f10 or f12.

---

### Post by elica on 2019-10-30
> **yancek said:**
> Your boot repair output shows 2 entries for windows.  The first one which has a menuentry line of:



should be the one that works as it should point to the boot file on the EFI partition (chainloader /efi/Microsoft/Boot/bootmgfw.efi).  The windows system partition is sdb3.

Remove the windows entry from /etc/grub.d/40_custom as it points to the wrong partition then run sudo update-grub.  Also, I see the message below in several places in the boot repair output which looks problematic.  Might try running chkdsk if you can get windows to boot.  I don't really know what the problem would be as I don't use windows.

So that's right, i got that message about NTFS and that's not good. I tried chossing as primary boot option the w10 disk and it does not load up anymore, the w10 restore utility come up with the blue screens. I would like to try to repair the NTFS disk and then try to fix the GRUB entries. The ntfs actually is not corrupted since the chkdsk does not show up any bad or corrupted sectors. Any ideas? Thanks guys !

---

