---
title: "Dual Booting Ubuntu &amp; Windows 7 - Windows not detected"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by thea2 on 2015-02-17
Hey guys,

First off, apologies if anything I say doesn't quite make sense - I am very much a theoretical computer scientist, I avoided computer architecture and OS courses at all costs! So I'm not entirely sure what I'm talking about here. Having said that...

I'm attempting to install Ubuntu on my Lenovo U410 Ideapad. I have disabled RAID and Intel Rapid Storage Technology. It has two harddrives, a 32G SSD and a larger HDD. Windows 7 Home Premium is currently installed on the HDD. However when I get to the Ubuntu installation type screen, it can't detect any operating systems. 
I attached an image of the disk managment program in Windows, and the options I get with the custom Ubuntu installation option (apologies for poor image quality).

I'm guessing dev/mapper/isw_egbfcigda_Volume0p1 is the System Reserved (F:) volume (although I don't understand why it appears twice) and the free space is my Windows 7 volume. 
I wanted to install Ubuntu on the 29.72GB of unallocated space on Disk 0 (seen in Windows disk managment), but I'm not sure what device that is. 

Here is the output of fdisk:

[FONT=arial]Disk /dev/sda: 32.0 GB, 32017047552 bytes[/FONT]
[FONT=arial]224 heads, 19 sectors/track, 14692 cylinders, total 62533296 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x1fc4b061[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT[/FONT]

[FONT=arial]Disk /dev/sdb: 750.2 GB, 750156374016 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=arial]Disk identifier: 0xb52306e2[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdb1   *        2048      411647      204800    7  HPFS/NTFS/exFAT[/FONT]
[FONT=arial]/dev/sdb2          411648  1370773503   685180928    7  HPFS/NTFS/exFAT[/FONT]
[FONT=arial]/dev/sdb3      1370773504  1424185343    26705920    7  HPFS/NTFS/exFAT[/FONT]
[FONT=arial]/dev/sdb4      1424185344  1464735743    20275200   12  Compaq diagnostics[/FONT]

[FONT=arial]Disk /dev/mapper/isw_egbfcigda_[/FONT][FONT=arial]Volume0: 64.0 GB, 64029458432 bytes[/FONT]
[FONT=arial]224 heads, 19 sectors/track, 29383 cylinders, total 125057536 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 131072 bytes / 262144 bytes[/FONT]
[FONT=arial]Disk identifier: 0x1fc4b061[/FONT]

[FONT=arial]                             Device Boot      Start         End[/FONT]
[FONT=arial]Blocks   Id  System[/FONT]
[FONT=arial]/dev/mapper/isw_egbfcigda_[/FONT][FONT=arial]Volume0p1   *        2048      206847[/FONT]
[FONT=arial]102400    7  HPFS/NTFS/exFAT[/FONT]

[FONT=arial]Disk /dev/mapper/isw_egbfcigda_[/FONT][FONT=arial]Volume0p1: 104 MB, 104857600 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 131072 bytes / 262144 bytes[/FONT]
[FONT=arial]Disk identifier: 0x00000000[/FONT]

[FONT=arial]Disk /dev/mapper/isw_egbfcigda_[/FONT][FONT=arial]Volume0p1 doesn't contain a valid partition table[/FONT]

[FONT=arial]Disk /dev/sdc: 4211 MB, 4211081216 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 511 cylinders, total 8224768 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0xb12c4313[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdc1   *         142     8224767     4112313    c  W95 FAT32 (LBA)


Any help on what my next step should be greatly appreciated. Thanks heaps.[/FONT]

---

### Post by oldfred on 2015-02-17
If it is seeing /mapper that is RAID (or LVM which Windows would not have).
I thought the new version of Ubuntu would not require the removal of the RAID meta-data as has been done with the older versions.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

This Lenovo has UEFI, but yours looks like it still is BIOS boot.

 Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

