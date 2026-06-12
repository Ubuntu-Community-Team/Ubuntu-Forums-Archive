---
title: "Installing Ubuntu 14.04 on existing Win10 (UEFI+GPT +secureboot scheme)"
date: 2015-12-28
forum: Installation &amp; Upgrades
---

### Post by Cbhihe on 2015-12-28
Hi, I'm about to set up a dual boot: Ubuntu 14.04 LTS x86_64 UEFI on a factory preset MS Win10 / UEFI / GPT. 

I have some experience installing several dual Trusty 14.04 LTS AMD64/i386 OSes on old WinXP's and Win7 running on legacy BIOS with MBR. However that experience is of little value to deal with UEFI firmware. At the same time many posts and a few good wikis are available, so I read a bit in the last 3 days.  I still have a few questions before I commit to my first dual boot install on Win10.

The box is a low cost HP laptop, just purchased for my little nephew as his first full-fledged PC.  
>>>  HP Notebook P4A24EA#ABF 
>>> CPU AMD A6-6310 1.8GHz + RAM 6GB + Graphics AMD  Radeon R4 + HDD 1TB + OS Windows 10 Family) with UEFI / GPT.

I drew from: 
- Wiki by @oldfred [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) 
 - comments by @RobinHood and @DanielB on being able to resize Win10 partitions with M$ Windows 10's Disk Management utility app. [https://superuser.com/questions/821131/is-it-safe-to-resize-windows-partition-with-gparted](https://superuser.com/questions/821131/is-it-safe-to-resize-windows-partition-with-gparted)
- "Creating an EFI partition" (paragraph) with `GParted`, when installing Ubuntu [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
- "How to create a bootable Ubuntu USB Flash Drive - unetbootin" (paragraph in post by @oldfred) [https://help.ubuntu.com/community/US...lation%20Media]("https://help.ubuntu.com/community/USB%20Installation%20Media")

What I did check/change already:
  - SecureBoot  enabled (ok for Ubuntu UEFI version > 12.04.2) 
  - FastBoot permanently disabled
  - Win10's EFI  partition correctly  identified just before the C:\, i.e. the NTFS partition containing Windows 10 OS
  - 445 GB storage space made available, syphoned off the C:\ volume, using the Disk Manager's own little shrink utilities.
  - checked the integrity of C:\ with `chkdsk` in Win10's PowerShell before and after shrink operation.
  - rebooted (no complaint on the part of the box)

**Question 1:** 
From the Ubuntu Community Help on UEFI:
> If you are manually partitioning your disk in the Ubuntu installer, you need to make sure you have an [EFI System Partition (ESP)]("http://en.wikipedia.org/wiki/EFI_System_partition") set up. This partition holds EFI-mode boot loaders and related files. 


[LIST]
[*]If your disk already contains an ESP (eg if your computer had Windows 8 preinstalled), it can be used for Ubuntu too. **Do not format it.** It is strongly recommended to have only 1 ESP per disk. 
[*]An ESP can be created via a recent version of [GParted]("https://help.ubuntu.com/community/GParted") (the Gparted version included in the 12.04 disk is OK), and must have the following attributes:
[LIST]
[*]*Mount point:*  /boot/efi  (remark: no need to set this mount point when using the  manual partitioning, the Ubuntu installer will detect it automatically) 
[*]*Size:* minimum 100Mib. 200MiB recommended. 
[*]*Type:* FAT32 
[*]*Other:* needs a "boot" flag. 
[/LIST]
         
[/LIST]

I do have Win10 pre-installed - I could identify the EFI on the HDD, located just before the C:/ volume. 
If `GParted` is going to recognize it automatically, does it mean I do NOT need to create a `/boot` partition for Linux (after selecting ?
(Not sure I completely understood the above quote.)

**Question 2:**
As I can see, the ESP set up in my Win10 box holds 260MB. I am used to my ext4 `/boot` partition in Linux being as large as 500MB (an overkill for most, I understand). 
If the two boot infos (from both the Win10 and the Linux distros) are combined in that ESP, even less space will be left for a user willing to accommodate different distro-installs in the boot menu. Is there a work around for that ? (except for doing clean up of course).
[B]
Questions 3:[/B]
From Win10, I plan on redefining Win10's "user folder" paths so they point to [FONT=courier new]/home[/FONT] on the soon to be created ext3 or ext4 partition on the Ubuntu OS side. I include my partitioning scheme below. NTFS is not a format option for [FONT=courier new]/home[/FONT].
 - Will Win10 be able to read/write in an ext3 or ext4 partition ? 
 - Or is the last resort using a specific [WinOS-side driver]("http://river (https://superuser.com/questions/465393/how-to-mount-read-write-an-ext4-partition-on-windows") for Win10 to be able to access an ext3 or ext4 volume ? 
This is how I usually do it for XP and Win7 and I am thinking (a) Paragon software offers ExtFS for Windows 2.0, (b) tune2fs, (c) [Ext2Fsd]("http://www.ext2fsd.com"). The latter when used in WinXP or Win7 only reads ext4 and in my experience produces quite a few write errors with ext3, to the point that I would label it unreliable.
- Is further advice available on that subject ?

Partitioning scheme (from left to right):
> **EFI-SP**    260MB (preinstalled Win10) 
**C:\**          470GB (after maximum shrinking of [FONT=courier new]C:[/FONT] for the preinstalled Win10) <- unfortunately I could not shrink [FONT=courier new]C:[/FONT] further due to unmovable Window files on that volume.
**[B]/**boot[/B]      500MB (ext4, _*but only*_ if /boot is not in EFI-SP above - *see question 1*)
**swap**       12 GB swap space        
**[B]/** [/B]70 GB root ext4
**[B]/**home[/B]    320 GB  ext3 or ext4
**[B]/**var[/B]        40 GB   ext4
**no flag**    744 MB  (preinstalled Win10 recovery space - no FS, not accessible)
**no flag**    15 GB  (preinstalled Win10 recovery space - no FS, not accessible)

Thanks. I'll use all the help I can get.    -ced

---

### Post by oldfred on 2015-12-28
Do not confuse an ESP with a /boot. They are totally different.
And most desktop installs do not need a /boot. With LVM full drive or full drive encrypted LVM you do need a /boot but full drive LVM erases entire hard drive including all of Windows & Windows recover partitions.
Keep /boot are part of / (root). I also suggest keeping /var as part of / especially if you have a / as large as you are suggesting. I normally use 25GB for / and actually use between 11 & 13GB of that. That also includes all of /home & /var. But do have all data in data partition. I used to use a shared NTFS, but once I shut down XP, all data is in a shared Linux formatted partition.

Windows will not read Linux formats. But NTFS driver reads NTFS partitions that are not hibernated, fast startup, or needing chkdsk. I consider the Linux NTFS driver as better choice than Windows Linux drivers. Often Windows drivers are read only as ownership & permissions are unique to Linux and Windows does not support those.
Best to have separate NTFS shared data partition. It worked even better with Windows 7 as 7 did not have the fast start up option. And Windows updates will probably reset that to on, creating issues. 
And Windows does not seem to have a way to unmount the shared data partition, but still best to have it. The Linux NTFS driver exposes all the normally hidden files & folders in Windows. And users may then make mistakes. I regularly turned on show those files & folders in XP and often had to make repairs as I would move mouse & click too quickly and move an entire system folder to the wrong place.

I now have multiple Ubuntu installs, one main working 14.04 and several newer versions to see differences/improvements. I link my data partitions into all installs.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Cbhihe on 2015-12-28
Thanks @oldfred ... again !

So `/boot` in *root* (`/`); ok, can be done.
However I do need `/home` and `/var` to be on separate volumes. 

I understand that `GParted` will actually put a `/boot/efi`tag on the FAT32 Win10 EFI partition without me doing anything. In that sense the Linux install process does recognize it deals with Win UEFI OS. That's cool.
I also accept that `/boot` and ESP are two different things, although I don't fully grasp the technicality of this. A readable reference on that would be great.

The problem with having an NTFS volume for data is any Linux user will have access to any data generated by other users, either from Win10 or from Linux in that volume. 
 Meanwhile the clunkier inverse solution, i.e. using a Win driver for Linux, allows Win users to see what a personalized symbolic link across file system (NTFS on Win side and ext3 on Linux side) lets them to. It means that Win users can be pointed to their part of the [FONT=courier new]/home[/FONT] tree on the Lx side (a good thing)... at the cost of poor write performance and again in my first-hand experience a large number of write-operation errors on the ext3 FS, supplemented by a very large CPU I/O overload. I repeatedly clocked CPU I/O at 100% sometimes for as much as 2 min on end when running trials with `ext2FSD`. Setup configuration was dual boot WinXP SP3 (NTFS) with Trusty Desktop 14.04.1 LTS (ext3). It is a poor cop-out. 
  
I see no good solution to this dilemma: it's "no permission for Linux files and free for all to see from Linux" vs. "poor, no reliable write operation for Windows". Unless.. I just had an idea and will report here later. It is after all possible to selectively mount _**part of**_ an NTFS volume from Linux, the which (part) could be made to depend on the logged user.... I don't fully know what the security implication of that would be. Must try.

---

### Post by oldfred on 2015-12-28
In my UEFI install, fstab mounts /boot/efi/EFI/ubuntu in /boot. So ESP - efi system partition becomes part of /boot. And /boot has to be Linux formatted and ESP must be FAT32 formatted. There are some advanced ways to use UEFI and have kernel in ESP to directly boot, but have not seen much on that.

From bottom of oldfred's link below on UEFI.
 ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)

 Technical info on Legacy BIOS and UEFI AMI AptioMar 2012 - 20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

Info on UEFI boot loaders from the author of rEFInd.
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

