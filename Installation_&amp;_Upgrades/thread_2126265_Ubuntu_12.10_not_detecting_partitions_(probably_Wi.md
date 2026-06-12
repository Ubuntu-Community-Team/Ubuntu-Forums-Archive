---
title: "Ubuntu 12.10 not detecting partitions (probably Windows 8's fault)"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by JJ452 on 2013-03-16
Hi,

I recently upgraded my PC - added an SSD and installed Windows 8 pro. I was able to install Windows 8 fine and leave 40GB of unallocated space for Ubuntu.

I download Ubuntu 12.10 64bit, burnt it onto a disk and attempted to install it. I followed some instructions I found and disabled fastboot and secureboot on my PC (I have a newish mobo with UEFI). The disk booted fine and I was able to get into the live CD version of Ubuntu and access all the files on the Windows 8 partition but when I tried to install Ubuntu the installer found no partitions on the SSD and listed the whole drive as free space (from the advanced tab when selecting where to install).

Am I doing something wrong? I find it odd that Ubuntu was able to mount the Windows 8 partition and let me access the files but the installer can't find anything on the drive.

 Any help would be greatly appreciated.

---

### Post by oldfred on 2013-03-17
From liveCD/DVD/Flash installer in live mode's terminal post this.

       sudo parted /dev/sda unit s print

You can also attach a screen shot of gparted with the paperclip icon  on the advanced editor (not quick reply).

---

### Post by JJ452 on 2013-03-18
Hi,

The output is actually a question:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?        

```

I have no idea if it's a GPT partition or not. I typed yes and got:

```
Model: ATA INTEL SSDSC2CW24 (scsi)
Disk /dev/sda: 468862128s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


```

and there is no output if I type no.

---

### Post by oldfred on 2013-03-18
If drive was gpt and you installed Windows in BIOS/MBR mode, it only converts primary gpt partition table. But gpt has a backkup partition table that Windows ignores, but then Linux tools see MBR and back up gpt and get confused. As your parted list says.

You probably have MBR(msdos), but really need to know to be safe. And you need to know how your are booting.
Both Windows and Linux now will install from the new UEFI/BIOS in either mode, but install based on how you boot installer. If you boot install flash drive in UEFI it installs in UEFI, if you boot in BIOS/Legacy/CSM it installs in BIOS mode.

But Windows only boots with UEFI with gpt partitions and from gpt partitions only boots with UEFI. Or with BIOS only with MBR partitions.
Ubuntu will boot from gpt partitioning with BIOS or UEFI. 
UEFI need gpt partitioning for both Windows & Ubuntu.

And both Windows & Ubuntu need to be installed in the same mode to easily dual boot. But some UEFI are not correct and only let you install Ubuntu in BIOS mode. And then you have to use Boot-Repair to convert to UEFI mode.

Confused yet? 

Does Windows still boot? Either BIOS mode or UEFI mode?

---

### Post by JJ452 on 2013-03-18
Very confused.... From what you said:
 

[LIST]
[*]I have both GPT and MBR tables and the installer doesn't know which one it should be working with and/or if both are in use.
[/LIST]


[LIST]
[*]UEFI needs GPT partition tables.
[/LIST]


[LIST]
[*]Windows only works with GPT/UEFI or MBR/BIOS
[/LIST]


[LIST]
[*]Ubuntu works with GPT and either BIOS or UEFI
[/LIST]

Have I got that right?

Windows boots fine but I'm not sure which mode I'm in. I thought that UEFI mode was the nice GUI you get on the MOBO but maybe there is more to it?

---

### Post by oldfred on 2013-03-18
It really is only UEFI on the mother board. But it has CSM which is BIOS mode.
       Compatibility Support Module (CSM), which emulates a BIOS mode, when booting 
    
Does this show MBR partitions or just complain about gpt. Fdisk only works with mMBR(msdos). You need gdisk for gpt drives.
sudo fdisk -lu

From Windows is this link like your partitioning or do you just have the 100MB (hidden) boot/repair and main partition? If you installed you will not have a vendor recovery.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

---

### Post by JJ452 on 2013-03-18
It did not prompt me like the last time. The output is:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9396a43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   389122047   194201600    7  HPFS/NTFS/exFAT
```


I checked the windows partitions and there is a 350MB system reserved partion and then one for Widnows and some unallocated space for Ubuntu.

---

### Post by oldfred on 2013-03-18
Then you should be able to use fixparts to remove the stray gpt data. You should then get the two partitions shown without the error messages. And only have MBR(msdos) partitions.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

if sfdisk will let you back up partition table run it first.
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

