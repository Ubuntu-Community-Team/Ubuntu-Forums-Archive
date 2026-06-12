---
title: "dual boot: Win10 after Ubuntu (and getting back into my pc-bsd partition)"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by rjvbertin on 2016-07-01
Hi,

I found an old thread outlining how to do a clean Win7 install alongside existing Linux installation(s). Basically, make sure the target partition is already in NTFS, and that you're in legacy/BIOS mode. And save your GRUB config somewhere so it can be reinstalled.

Is that still accurate with the Win10 installer? I have
- a recent notebook with UEFI boot disabled
- an SSHD with GPT pmap, 200Mb EFI partition first, with 1 free partition I could use for Win10 evaluation.
- a bootable USB thumb drive with last week's Win10 iso burned onto it.

I used that drive to upgrade a notebook's Win7, and was pleasantly surprised to see that was an almost perfectly transparent exercise. The Linux partitions on that rig weren't touched, and I didn't even have to reinstall GRUB (result: it still offers me an option to boot into Win7 :))
That disk has an MBR pmap though, and also has a dedicated recovery partition (which was updated).

As a bonus question while I'm at it: does anyone have a good suggestion on how I could get grub to access my PC-BSD partition? Following the suggestions for a tailored etc/grub.d/40_custom only gives me a loader error that `/boot/loader` doesn't exist.

---

### Post by oldfred on 2016-07-01
Windows only installs in BIOS boot mode to MBR(msdos) partitioned drives.
Windows only installs in UEFI boot mode to gpt(GUID) partitioned drives.
Ubuntu can boot in either UEFI or BIOS from gpt if correct supporting partitions are on drive. 

Windows 7 default install from DVD is BIOS mode only.
But it can be copied to flash drive and a few files moved around to create the /EFI/Boot/bootx64.efi which is the filename (different actual file by system) that all external installers use.

        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html

      [/URL]
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

If you have new UEFI hardware, you are installing a 35 year old BIOS/MBR configuration. 

       
         GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 
    
    [URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]
[/URL]

---

### Post by rjvbertin on 2016-07-01
That's a bit TMI ...

I don't particularly mind putting the machine back in UEFI mode in order to install and/or boot MS Windows, esp. if that allows to keep Grub and the "Windows bootloader" separate. 

FWIW, this is my partition map;

> Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A9B02C17-CDB3-43A7-BD5E-B3CF38B87B2F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 8-sector boundaries
Total free space is 32749 sectors (16.0 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI
   2          409640          411687   1024.0 KiB  EF02  GPT Boot Partition
   3          411904        33966335   16.0 GiB    8200  swap
   4        33966336       640043263   289.0 GiB   8300  bolaLNX
   5       640043264       744900863   50.0 GiB    8300  bolaLNX2
   6       744900864       745949439   512.0 MiB   8300  bolaBoot
   7       745949440       972644607   108.1 GiB   A504  bolaBSD
   8       972644608       976740607   2.0 GiB     A502  




A priori that EFI partition is big enough to serve as a Win10 bootloader; I've already used Win2USB and Win2HDD to clone an existing Win10 install to another disk with a comparable partition map. Main reason I'm now trying a fresh install is that even Win2HDD made a clone that wouldn't use the actual graphics driver instead of some generic MS device. (And the main reason to consider installing to my current boot disk that the notebook is a RPITA to open.)

So, if the installer will happily take the EFI and bolaLNX2 partitions above (after converting bolaLNX2 to an msdata/NTFS partition) then I should be fine, no?

---

### Post by oldfred on 2016-07-01
Do not know about BSD? Does it have UEFI boot mode?

But if you install Windows in BIOS boot mode with MBR it either will not install or totally erase drive in converting MBR. And it does not correctly convert to MBR as it leaves backup gpt partition table and then Linux tools see both MBR & gpt and assume drive is corrupted and want to erase it. You can fix it if you really want MBR with fixparts.

Windows wants the system reserved, and it must be before first NTFS. See links above. But it will work without system reserved until you run some software that requires DRM and that writes serial numbers or other data into system reserved.

For both Windows & Ubuntu how you boot installer, UEFI or BIOS is then how it installs. But the choice for the USB installer may not be default boot mode in UEFI for the actual install. Just be consistent and always boot UEFI (or always CSM).

---

