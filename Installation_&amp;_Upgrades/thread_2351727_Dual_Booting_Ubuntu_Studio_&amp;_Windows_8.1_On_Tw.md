---
title: "Dual Booting Ubuntu Studio &amp; Windows 8.1 On Two Hard Drives"
date: 2017-02-06
forum: Installation &amp; Upgrades
---

### Post by Dynamata on 2017-02-06
I have a 240GB SSD, 1TB HDD, 8GB RAM, ASUS B85-PRO GAMER MB ([COLOR=#545454][FONT=arial]UEFI [/FONT][/COLOR][COLOR=#6A6A6A][FONT=arial]**BIOS**[/FONT][/COLOR]). I plan to install Windows 8.1 & Ubuntu Studio 16.04.1.

[COLOR=#242729][FONT=Arial]**sda** (SSD):[/FONT][/COLOR]

[LIST]
[*]40 GB partition for Ubuntu
[*]200 GB free space ( - Unallocated space at end)
[/LIST]
[COLOR=#242729][FONT=Arial]**sdb** (Hard Drive):[/FONT][/COLOR]

[LIST]
[*]500 GB partition for Windows
[*]500 GB partition for Ubuntu Home ( - Unallocated space at end)
[/LIST]
Does this look OK, where is the best place to locate swap & does it need to be 16GB ? I will install Windows first. An existing walk-through for this type of setup would be useful. :)

---

### Post by yancek on 2017-02-06
Dual booting windows and Ubuntu UEFI is explained in detail at the Ubuntu documentation site below.  Are both drives internal drives?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Dynamata on 2017-02-06
Internal via hot swap drive bays, thanks for the link. :-)

---

### Post by oldfred on 2017-02-06
With UEFI make sure drives are partitioned gpt.
Windows in UEFI mode on gpt requires several extra partitions.
I still think Windows is better as first drive, Ubuntu is more flexible except on install of grub in UEFI mode. Then grub has to install to the ESP - efi system partition on sda. 

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Make sure when connecting drives you start at SATA0 and plug drives in SATA port order. SATA0 drive will be sda.
I have skipped ports and had a DVD in between drives and had lots of issues. Device like /dev/sdb can change when plugging in flash drives and manual boot issues of which drive is hd0 and hd1 from UEFI/BIOS and grub.

       
 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
Swap only needs to be 2 or 3GB just to have some. But it probably will never be used, if 4GB of RAM.
With 17.04 they are changing from swap partition to swap file.

---

