---
title: "Can someone verify my plan to install Ubuntu for a dual boot?"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by drpeppercan on 2018-08-24
I just installed Win10 in my 1Tb HD.
I also have a 125Gb SSD drive, that has (or used to have) Win10. Not presently in the computer.
I was thinking of replacing the HD with the SSD, then boot off of an Ubuntu Life USB drive.
With Gparted format the SSD drive. Then install Ubuntu there.
Then bring back the HD drive and have both in the computer.
When starting, should I expect Grub recognizing both. Or should some extra work be needed, maybe with the help of Boot Repair Disk?

Or should I scratch the whole plan above and go with somebody else's suggestions?

Thanks guys!

---

### Post by oldfred on 2018-08-25
Newer UEFI system?
And then did you install Windows in UEFI boot mode or 35 year old BIOS/MBR configuration?
You  must install Ubuntu in same boot mode for grub to be able to find & boot Windows.
How you boot install media, UEFI or BIOS is then how it installs.
        [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
More details in link in my signature below.

But grub only boots working Windows. Or Windows that does not need chkdsk, nor is hibernated. And fast start up is always on hibernation. And Windows will keep turning it back on with updates, so when grub does not boot it, you need your Windows repair disk with repair console. Or maybe directly boot from UEFI and f8 into repair console.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If both are UEFI, and Windows fast start up is off. This should add Windows to grub menu.
sudo update-grub

---

### Post by drpeppercan on 2018-08-25
Hi oldfred,

I do not know in which mode Win10 got installed.
I can tell you that I did go into BIOS every time I needed to change the USB drive, to ensure that the pc would boot off of the right drive. And to keep the Windows Boot Manager disabled (just in case). And lastly I can say that Win10 did install from a USB drive. I hope that tells you enough to tell.

---

### Post by oldfred on 2018-08-25
Post these:
sudo parted -l
sudo gdisk -l /dev/sda
If not sda do this also
sudo gdisk -l /dev/sdb

That will show if drive is MBR(msdos) or gpt(GUID). Windows only boots from gpt with UEFI and from MBR with BIOS. How you boot install media UEFI or BIOS, is then how it installs for both Windows & Ubuntu.

---

### Post by drpeppercan on 2018-08-25
I used the Live USB drive.

1.
sudo parted -l
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32        EF    boot, esp
 2      538MB   1000GB  1000GB  ntfs               msftdata




Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start  End     Size    Type     File system  Flags
 1      106MB  2000GB  2000GB  primary  ntfs




Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdc: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      65.5kB  4010MB  4010MB  primary  fat32        boot, lba




2.
sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.3


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Model: WDC WD10EZEX-21M
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 1B1FA484-E02B-4FAA-906D-10D3D588B00B
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  EF
   2         1050624      1953523711   931.0 GiB   0700  


3.
sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.3


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Disk /dev/sdb: 3907029168 sectors, 1.8 TiB
Model: External USB 3.0
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): D5635417-63AB-43F9-8070-8593586567F6
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 211884 sectors (103.5 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1          206848      3907024064   1.8 TiB     0700  Microsoft basic data

---

### Post by drpeppercan on 2018-08-25
It seems I used MBR.
At least for the next time, how is it done with UEFI? I know this pc has it, it's only just less than 2 years old.

---

### Post by ubfan1 on 2018-08-25
The 1T drive is gpt, with an EFI partition, so Windows install there and running would be in UEFI mode.  The 2T drive must be for data, and that partitioning doesn't matter.

---

### Post by oldfred on 2018-08-25
Your sda, the 1TB drive is gpt, but external USB drive is MBR.

With gparted it is the very first thing you do.
        I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. 
    
You can also convert drive, but must have good backups as sometimes conversion does not go well.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

You do not have what looks like a typical Windows partitioning.
       
 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by drpeppercan on 2018-08-25
Oh, right! It's the partition type what makes it run in one way or the other!
Admittedly, I should have unplugged that ext USB drive before I ran the commands.
I'll install Ubuntu in a SSD drive that's not in the pc yet.
So as long as I format it to an EFI partition it'll all be ok, right?

---

### Post by oldfred on 2018-08-25
With multiple drives and willing to unplug drive that is often a lot easier.
How you boot install media, is how it installs. It will convert drive to correct partitioning potentially erasing data. Always have good back ups. 
See also link in my signature below. Nine "easy" steps to install.

I do not unplug drives, but have to partition in advance with gpt & an ESP on second or external drives and reconfigure boot files booting as UEFI & grub just have certain rules and multiple drives is not assumed as common.

---

### Post by drpeppercan on 2018-09-15
It turns out the easiest way to set up the dual boot was as follows:
[LEFT][COLOR=#000000][FONT=&amp][LEFT]
[SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Calibri]This assumes one SSD (120 Gb) and one HD (1 Tb).[/FONT][/COLOR][/COLOR][/SIZE][/LEFT]

[LIST=1]
[*][LEFT][SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Calibri]Install Linux on SSD, while HD is unplugged.[/FONT][/COLOR][/COLOR][/SIZE][/LEFT]

[*][LEFT][SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Calibri]Swap drives to install Win10 on the HD, [/FONT][/COLOR][COLOR=#000000][FONT=Calibri]while SSD is unplugged.[/FONT][/COLOR][/COLOR][/SIZE][/LEFT]

[*][LEFT][SIZE=3][COLOR=#000000][[FONT=Calibri]Install rEFInd[/FONT]]("https://sourceforge.net/projects/refind/")[COLOR=#000000][FONT=Calibri] in Windows 10 (See instructions below).[/FONT][/COLOR][/COLOR][/SIZE][/LEFT]

[*][LEFT][SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Calibri]Plug the SSD with Linux.[/FONT][/COLOR][/COLOR][/SIZE][/LEFT]

[*][LEFT][SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Calibri]Boot up.[/FONT][/COLOR][/COLOR][/SIZE][/LEFT]

[*][LEFT][SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Calibri]If rEFInd doesn't show, go to the BIOS and swap the order of the drives.[/FONT][/COLOR][/COLOR][/SIZE][/LEFT]

[*][LEFT][SIZE=3][COLOR=#000000][COLOR=#000000][FONT=Calibri]Done![/FONT][/COLOR][/COLOR][/SIZE][/LEFT]
[/LIST]

What you put and where it's really up to you, it depends on your situation. For my situation, I needed to move Windows to the largest drive available.

**Install rEFInd in Windows 10.**
[/FONT][LEFT][COLOR=#000000][FONT=Calibri]
[LIST=1]
[*=left][COLOR=#000000][FONT=Calibri]Get [/FONT][/COLOR][[FONT=Calibri]rEFInd[/FONT]]("https://sourceforge.net/projects/refind/")[COLOR=#000000][FONT=Calibri].[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri]Expand the ZIP file, and copy the resulting folder to C:[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri]Open Command Prompt Admin[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri]Enter this command line: **[FONT=courier new]Mountvol[/FONT]****[FONT=courier new] S: /S[/FONT]**[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri]In the same terminal move two levels up to C:[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri][LEFT][COLOR=#000000][FONT=Calibri]Enter this command line: [/FONT][/COLOR][/LEFT]
**xcopy /E refind-bin-0.11.3 S:\efi\refind\ **(accommodate the version number to the one you got)[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri]Go to the previouly mounted drive: S:[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri][LEFT][COLOR=#000000][FONT=Calibri]Enter this command line: [/FONT][/COLOR][/LEFT]
**[FONT=courier new]cd EFI\[/FONT]****[FONT=courier new]refind\refind[/FONT]**[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri][LEFT][COLOR=#000000][FONT=Calibri]Enter this command line: [/FONT][/COLOR][/LEFT]
**[FONT=courier new]rename [/FONT]****[FONT=courier new]refind.conf-sample refind.conf[/FONT]**[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri][LEFT][COLOR=#000000][FONT=Calibri]Enter this command line: [/FONT][/COLOR][/LEFT]
**[FONT=courier new]bcdedit[/FONT]****[FONT=courier new] /set {bootmgr} path \EFI\refind\refind\refind_x64.efi[/FONT]**[/FONT][/COLOR]
[*=left][COLOR=#000000][FONT=Calibri]Done![/FONT][/COLOR]
[/LIST]
[/FONT][/COLOR][/LEFT]

[/COLOR][/LEFT]

---

