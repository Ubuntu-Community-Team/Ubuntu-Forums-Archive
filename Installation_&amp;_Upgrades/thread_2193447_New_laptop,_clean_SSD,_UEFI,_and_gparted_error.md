---
title: "New laptop, clean SSD, UEFI, and gparted error"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2013-12-12
I've successfully installed 13.10 on a new Dell laptop, with a clean aftermarket SSD. The install went fine. But, when I run gparted on the SSD, I get the following:
"The backup GPT table is not at the end of the disk...."  Fix, cancel, ignore.

I've read up a bit on EFI, GPT, installing Ubuntu in EFI mode, etc., but can't figure out what this error is about, and if I should:
a) trust Gparted to fix it,
b) install EFI partitions via the directions here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
or ???

(FYI, I ran boot-repair and it did not find a EFI section on the SSD)

TIA

---

### Post by drmrgd on 2013-12-13
Are you dual booting, or is Ubuntu the only OS on your laptop?  That may not matter, but might be a clue.  

I've not seen this before, but I did find this (which you may have already seen) suggesting that it may be the way the disk is set up if it's in a RAID configuration (in this case probably not correctly) or if HPA is enabled.  Have a look and see if you can get any clues in there:

[http://askubuntu.com/questions/266019/ubiquity-doesnt-find-my-partitions](http://askubuntu.com/questions/266019/ubiquity-doesnt-find-my-partitions)

---

### Post by fantab on 2013-12-13
> "The backup GPT table is not at the end of the disk...."  Fix, cancel, ignore.


Fix it. Tell us how it goes.

---

### Post by aeronutt on 2013-12-13
Thanks for the help so far. I'll read the recommended resourses. More info:

- Laptop, with 1 SSD aftermarket disk installed. (OEM disk with W8 removed/replaced with SSD. I'm proud to say that I didn't boot W8 one single time from the OEM disk. :))
- Single boot.
- This error popped up on the clean SSD disk as it came from Samsung (no image/reformatting/partitioning had been done).
- This error still occurs after loading 13.10 when running Gparted. The error did NOT occur when I formated/partitioned the disk during the 13.10 install.
- Also interesting; when I first booted 13.10 from USB, I ran gparted on the OEM disk, and the exact same gparted error was reported on the OEM disk with W8 as delivered by Dell. 

With the above additional info, could this be something in the BIOS, BIOS settings? Seems odd.

---

### Post by fantab on 2013-12-13
Ok... Do you have UEFI or BIOS? To what mode is it set to?
Look for SATA mode in UEFI/BIOS and tell us what you have?
Have you tried, "Try Ubuntu without installing" option? Does it boot well? If you are able to 'Try Ubuntu' the open Terminal [ctrl+alt+T] and post the output of the following commands:

```
sudo parted -l
```

---

### Post by oldfred on 2013-12-13
For issues with gpt drives, I also like to see what gdisk says. I have always partitioned in advance with gparted and not had issues.

sudo apt-get install gdisk
 sudo gdisk -l /dev/sda

If you do not have an efi partition do you then have a bios_grub partition and installed in BIOS/CSM/Legacy boot mode? How you boot installer UEFI or BIOS is how it installs.

---

### Post by aeronutt on 2013-12-13
> **fantab said:**
> Ok... Do you have UEFI or BIOS? To what mode is it set to?
Look for SATA mode in UEFI/BIOS and tell us what you have?
Have you tried, "Try Ubuntu without installing" option? Does it boot well? If you are able to 'Try Ubuntu' the open Terminal [ctrl+alt+T] and post the output of the following commands:

```
sudo parted -l
```
UEFI or BIOS: UEFI (set to UEFI) and "Load Legacy Option Rom, Enabled"
SATA: AHCI  
Boots fine from USB or HDD (successfullly installed on SSD)

output of sudo parted -l (after booting from SSD):

Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  4000MB  3999MB  primary  linux-swap(v1)
 2      4000MB  16.0GB  12.0GB  primary  ext4            boot


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? ok                                                             
Warning: Not all of the space available to /dev/sdb appears to be used, you can
fix the GPT to use all of the space (an extra 45756080 blocks) or continue with
the current setting? 
Fix/Ignore? i                                                             
Model: ATA LITEONIT LMS-32L (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  8589MB  8588MB               Basic data partition

---

### Post by aeronutt on 2013-12-13
> **oldfred said:**
> For issues with gpt drives, I also like to see what gdisk says. I have always partitioned in advance with gparted and not had issues.

sudo apt-get install gdisk
 sudo gdisk -l /dev/sda

If you do not have an efi partition do you then have a bios_grub partition and installed in BIOS/CSM/Legacy boot mode? How you boot installer UEFI or BIOS is how it installs.

sudo gdisk -l /dev/sda:

GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.
***************************************************************

Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 457148717 sectors (218.0 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         7813119   3.7 GiB     8200  Linux swap
   2         7813120        31250431   11.2 GiB    8300  Linux filesystem

---

### Post by oldfred on 2013-12-13
That is not good that parted says it is gpt and gdisk says it it MBR???

If you want to boot in UEFI mode you must have gpt, and you also need an efi partition. It generally should be first and 200 to 350MB. 
You can also use gpt and boot in BIOS mode with Ubuntu if you add a bios_grub partition.

But Windows only boots from gpt partitioned drives with UEFI.
Both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.

Which do you want? We need to fix partition table to be correct for one or the other and if gpt add the necessary efi or bios_grub partitions.

---

### Post by fantab on 2013-12-13
> Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  4000MB  3999MB  primary  linux-swap(v1)
 2      4000MB  16.0GB  12.0GB  primary  ext4            boot


> 
Partition table scan:
  **MBR: MBR only**
  BSD: not present
  APM: not present
  GPT: not present


**************************************************  *************
[B]Found invalid GPT and valid MBR; converting MBR to GPT format
in memory[/B].

> UEFI or BIOS: UEFI (set to UEFI) and "Load Legacy Option Rom, Enabled"

All the above indicates that you are NOT booting in UEFI; you ARE booting in 'legacy/BIOS/CSM/MBR' mode.
Ideally you should install OS and boot it in UEFI mode if you have newer hardware.. 

Problem: You have MBR/msdos partition table, but there is a GPT backup table on the disk. This confuses GRUB and cause issues.

The following are your options:
1. Remove 'backup GPT data' with [**FIXPARTS**]("http://www.rodsbooks.com/fixparts/"), and continue with 'Legacy/MBR' boot.
Or
2. Convert the SSD to GPT and re-install Ubuntu to boot in UEFI mode. [Recommended]

If you opt for option '2.' then:
(i)   Run 'Fixparts' on the SSD and remove Backup GPT data.
(ii)  [Boot with Ubuntu DVD/USB in EFI mode only]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode"), 'Try Ubuntu Without installing' and Open Gparted.
(iii) Using Gparted 'create a new Partition table' GPT. 
In Gparted, navigate to 'Devices' -> '*create new partition table*' -> 'Advanced' -> GPT (GUID Partition Table), 'Apply changes'.
(iv) Recreate Partitions, (you can consider the following suggestion):
500mb FAT32 'boot' flag (EFI partition)
20Gb Ext4 '/' (Ubuntu system files)
4Gb SWAP
All the remaining GB Ext4 (either a simple Data partition or /home).
Close Gparted.
(v) Install Ubuntu from Desktop.
(vi) During Install, at the '*Installation Type*' dailog choose '**Something Else**' option to manually direct the install to correct partition, 25Gb.
After you choose 'Something Else', in the next dialog select the 25Gb partition and use following settings:
Use As : Ext4 journaling system...
Mountpoint : /
Format: select it.

If you want to use your DATA partition as '/home then:
Use as: Ext4
Mountpoint: /home
Format: yes.

Apply changes, continue with installation and finish it.

Thats it.

---

### Post by aeronutt on 2013-12-14
> **oldfred said:**
> That is not good that parted says it is gpt and gdisk says it it MBR???

If you want to boot in UEFI mode you must have gpt, and you also need an efi partition. It generally should be first and 200 to 350MB. 
You can also use gpt and boot in BIOS mode with Ubuntu if you add a bios_grub partition.

But Windows only boots from gpt partitioned drives with UEFI.
Both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.

Which do you want? We need to fix partition table to be correct for one or the other and if gpt add the necessary efi or bios_grub partitions.

I'd prefer UEFI.

---

### Post by aeronutt on 2013-12-14
> **fantab said:**
> All the above indicates that you are NOT booting in UEFI; you ARE booting in 'legacy/BIOS/CSM/MBR' mode.
Ideally you should install OS and boot it in UEFI mode if you have newer hardware.. 

Problem: You have MBR/msdos partition table, but there is a GPT backup table on the disk. This confuses GRUB and cause issues.

The following are your options:
1. Remove 'backup GPT data' with [**FIXPARTS**]("http://www.rodsbooks.com/fixparts/"), and continue with 'Legacy/MBR' boot.
Or
2. Convert the SSD to GPT and re-install Ubuntu to boot in UEFI mode. [Recommended]

If you opt for option '2.' then:
**(i)   Run 'Fixparts' on the SSD and remove Backup GPT data.**
(ii)  [Boot with Ubuntu DVD/USB in EFI mode only]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode"), 'Try Ubuntu Without installing' and Open Gparted.
(iii) Using Gparted 'create a new Partition table' GPT. 
In Gparted, navigate to 'Devices' -> '*create new partition table*' -> 'Advanced' -> GPT (GUID Partition Table), 'Apply changes'.
(iv) Recreate Partitions, (you can consider the following suggestion):
500mb FAT32 'boot' flag (EFI partition)
20Gb Ext4 '/' (Ubuntu system files)
4Gb SWAP
All the remaining GB Ext4 (either a simple Data partition or /home).
Close Gparted.
(v) Install Ubuntu from Desktop.
(vi) During Install, at the '*Installation Type*' dailog choose '**Something Else**' option to manually direct the install to correct partition, 25Gb.
After you choose 'Something Else', in the next dialog select the 25Gb partition and use following settings:
Use As : Ext4 journaling system...
Mountpoint : /
Format: select it.

If you want to use your DATA partition as '/home then:
Use as: Ext4
Mountpoint: /home
Format: yes.

Apply changes, continue with installation and finish it.

Thats it.

Attempting to use your excellent guidance, and when I run fixparts, it doesn't find any misplaced GPT data (as described on the tutorial page [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/))

Also, I changed a few settings in EUFI/BIOS (whatever I should call that :)), and gparted still produces an error, but it has changed slightly to :
"The backup GPT tabel is corrupt, but the primary appears OK, so that will be used."

Again, thanks for the help so far.

UPDATE: I just realized there's a /dev/sdb partition on the SSD!?  It's 29.82 GB, with 8GB showing as /dev/sdb1 (file system unknown) and 21.82 GB unallocated. Thoughts?

---

### Post by aeronutt on 2013-12-14
More info added to above thoughts. I ran
sudo gdisk -l /dev/sdb, and got:


> GPT fdisk (gdisk) version 0.8.7

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sdb: 62533296 sectors, 29.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 16777182
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        16775167   8.0 GiB     8400  Basic data partition

So, on a new SSD, there's 
/dev/sda, that appears to be a MSDOS/MBR disk, and
/dev/sdb, that appears to be a GPT disk that has a corrupted and/or misplaced backup GPT section.

I'm very confused, but I started out that way. :)

---

### Post by aeronutt on 2013-12-14
And one more thing, running "sudo lshw -C disk" results below.
Am I reading this right....there's something other than my Samsung SSD that looks like a disk, and is configured as a GPT disk???
Does this have something to do with the fact that the OEM disk was a magentic disk with an SSD cache? And even though that's removed, the BIOS needs to think it's there?

> sudo lshw -C disk
  *-disk                 
       description: ATA Disk
       product: Samsung SSD 840
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: EXT0
       serial: S1DBNSADA73680P
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=000b45ed
  *-disk
       description: ATA Disk
       product: LITEONIT LMS-32L
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: DM51
       serial: TW0H9R7V5508537G5186
       size: 29GiB (32GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=f5810abb-571a-4e28-93c1-3d9037f0d668 sectorsize=512



---

### Post by oldfred on 2013-12-14
Some Ultrabook type systems do not have the small SSD on hard drive but have one soldered onto the motherboard. It that what you have?

That would just give you a bit more space to work with. Often then users have installed / (root) onto the SSD and data or /home partitions on hard drive and gotten most of the advantages of SSD.

I am not sure that you have to run fixparts or even do any repairs if you want to totally reinstall in UEFI mode. I do prefer to partition in advance.
       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

I think fantab gave you what you need, but I will add my standard suggestion. But every user has his own needs and how to partition then is very personal. I find my own optimal partition plan is not so good a year or two later as I have changed what I want.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by aeronutt on 2013-12-14
Bingo, looks like I have an 'mSATA' device (shows up in the BIOS view screen). I assume it's as you describe, soldered to the motherboard. Now some things are starting to make sense. (I wished I known this earlier, I probably wouldn't have purchased an aftermarket SSD !!!!, I assumed the SSD was physically part of the HD, and that I could not use the OEM SSD as boot...oh well!)

So here's the way I read this as it stands:

- I have a mSATA at 32G, which due to orignal use (cache for HD), is configured in an odd way (GPT, but with some portion 'unusable' as seen by linux.)
- I have a SATA SSD disk currently set up as MBR/MSDOS, mainly due to 'corrupt' backup GPT.

I also prefer to partition in advance. I'm going to leave the mSATA device as is and not use it for now, configure the SATA SSD as EUFI, and reinstall. I'll let you know how it turns out!

---

### Post by oldfred on 2013-12-14
The Intel SRT uses RAID (somehow) and that leaves meta-data on drives. You can remove meta-data if not using the Intel SRT. I think now Ubuntu sees the RAID and lets installs take place but then grub still does not see it correctly as a RAID install of grub is a lot different. And some have reimplemented the SRT after install, so removing the meta-data does not permanent harm a Intel SRT.

 Even if raid not used BIOS may have set parameters, Also check BIOS settings
You only need it on the built in drive, if sdb run this:
sudo dmraid -E -r /dev/sdb

One or two users with the larger SSD like yours found the cache only used part of the SSD and turned SRT on and still had room for a 16GB / (root).

---

### Post by aeronutt on 2013-12-14
Ok, update. We're getting there, but still some problems.

- **[UPDATE...this is fixed. I turned 'secure boot' ON, and now am booting from USB into EFI mode]** I can't seem to boot from USB in EFI mode. Turning off all legacy options in BIOS screen (with only EFI on), the machine will not boot from USB. Turning on "load legacy ROM", then it boots from USB, but in legacy mode (as shown by this command: [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD")

- I used gparted to reconfigue the SSD as GPT drive, and while it looks like it was successful (option for GPT click, 4 primary partitions and 1 swap, all went well), when I run "parted -l", I STILL get "backup GPT table is corrupt, primary ok". Also, fixdisk does not fix this. Fixdisk simply states "this disk appears to be a GPT disk, Use GNU parted or GPT fdisk on it!"

---

### Post by oldfred on 2013-12-14
You should then use gdisk and its w command to write a update to partition table.

       Use gdisk and verify partitions are correct with p, and use w to write the partition table. The v command can give more details on issues if necessary.  If not correct just use q to quit. The w -write should update primary, backup & protective MBR.

   sudo gdisk /dev/sda
Command (? for help): 

   More info:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by aeronutt on 2013-12-14
gdisk shows nothing wrong. 
parted (and gparted) still shows corrupted backup table.
Dare I write table to disk using gdisk 'w' command?

gdisk:
> ubuntu-gnome@ubuntu-gnome:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): FFC97073-468C-4DE1-95DE-B8830374DE5A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 454604929 sectors (216.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   0700  EFI System Partition
   2         1026048         9218047   3.9 GiB     8200 
   3         9218048        33794219   11.7 GiB    8300 

Command (? for help): 

parted:
> ubuntu-gnome@ubuntu-gnome:~$ sudo parted -l /dev/sda
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  525MB   524MB   fat32           EFI System Partition  msftdata
 2      525MB   4720MB  4194MB  linux-swap(v1)
 3      4720MB  17.3GB  12.6GB  ext4


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? ok                 



---

### Post by oldfred on 2013-12-14
If partitions look good I would use the w command. I am surprised that parted gives error but gdisk does not.

Since you have a larger SSD, I might make / a bit larger. I just have Ubuntu on my 64GB SSD and created two / partitions, current install and test/future. But my current install uses about 10GB of which 2GB is /home mostly .wine, but all other data in in /mnt/data partition on rotating drive.

---

### Post by aeronutt on 2013-12-14
First, THANKS for all the help, I would have given up and returned the laptop, no doubt.

So get this. I ran gdisk and executed the 'w' command, and it certainly appeared to update/write the GPT sections.
Rebooted, and parted still says GPT backup is bad!! Possible bug in parted or gdisk command?

Is there a third way to check? (in addition to gdisk and parted?)

And yea, I usually have 2 or 3 partitions for some version of Linux..one stable, 2 others for testing versions. Then a large data partition that I backup.

---

### Post by oldfred on 2013-12-14
I think those two are the only ones that work with gpt partitioned drives.  Everything else is MBR based still.
If you use gparted does it also have the same error? I think is still is parted underneath the gui.

---

### Post by aeronutt on 2013-12-14
Yes, same error using gparted.

---

### Post by aeronutt on 2013-12-14
Follow up question:

- If I'm never booting Windows, can/should I create the efi boot partition as FAT32 or EXT4?

---

### Post by fantab on 2013-12-14
EFI is always FAT32, but I've also seen it as NTFS however rare. If dual booting with linux it has to be FAT32.

---

### Post by aeronutt on 2013-12-14
Thanks, I'll leave it as FAT32, and marked this as solved!! (Even with the descrepancy between 'parted' and 'gdisk'.)

Thanks again for all the great and timely help!!

---

### Post by fantab on 2013-12-14
> **aeronutt said:**
> gdisk shows nothing wrong. 
parted (and gparted) still shows corrupted backup table.
Dare I write table to disk using gdisk 'w' command?



GPT disks keep a backup of the partition table. It is this table that is corrupt. So if 'rewrite' the backup table with a good 'primary' table then that error will be made good.

Gdisk with '**w**' option does exactly that, it rewrites the backup table.
It should fix the error.

---

### Post by aeronutt on 2013-12-14
> **fantab said:**
> GPT disks keep a backup of the partition table. It is this table that is corrupt. So if 'rewrite' the backup table with a good 'primary' table then that error will be made good.

Gdisk with '**w**' option does exactly that, it rewrites the backup table.
It should fix the error.

Well, after running gdisk, and using the 'w' command, gparted/parted still shows an error, gdisk does not. So there's still a decrepancy between what gdisk and parted are reporting.

---

### Post by oldfred on 2013-12-15
The author of gdisk posts in askubuntu. I might post a question there with gdisk/parted error inconsistency  in title and see if he responds.
Explain or post the outputs from both gdisk & parted. And that you have done the w with gdisk to fix it.

---

### Post by aeronutt on 2013-12-15
Great idea.

[http://askubuntu.com/questions/391312/gdisk-vs-parted-error-inconsistency](http://askubuntu.com/questions/391312/gdisk-vs-parted-error-inconsistency)

---

