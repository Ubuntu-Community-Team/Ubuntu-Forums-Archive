---
title: "Would like help writing fstab for a GPT SSD"
date: 2022-09-22
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-09-22
I have never written a fstab for a GPT SSD, and would like some help.  Right now, I use nemo to mount the partitions that hold my data.  However, SpiderOakOne is not recognizing them; and thus, it is not backing them up.  The output of disks (gdisks) is shown below.  The first three lines for each partition are from "bar chart" of the SSD.  The next four lines are Size, Contents, Device, UUID, and Partition Type.  I hope I don't offend anyone by asking for this help, but it is used for most of my work.  It is dual-boot Ubuntu Unity 22.04 and Windows 11 Pro Insider Build.  Thank you, John

Recovery
Partition 1
523 MB NTFS
523 MB (523,239,424 bytes)
NTFS — Not Mounted
34140D7B140D417A
Microsoft Windows Recovery Environment

System
Partition 2
104 MB FAT
104 MB — 43 MB free (58.2% full)
FAT (32-bit version) — Mounted at /boot/efi
C60D-9EBB
EFI System

Partition 3
Unknown
/dev/nvme0n1p3
Microsoft Reserved

Local Disk
Partition 4
138 GB NTFS
136 GB — 63 GB free (53.9% full)
NTFS — Mounted at /media/john/Local Disk
CC220E26220E165C
Basic Data

Ubuntu
Partition 5
64 GB Ext4
64 GB (64,322,797,568 bytes)
Ext4 (version 1.0) — Not Mounted
/dev/nvme0n1p5
15ac3139-08d5-eba3-3c1d-a9ee17a319d8
Basic Data

File System
Partition 9
75 GB Ext4
75 GB — 46 GB free (38.8% full)
Ext4 (version 1.0) — Mounted at Filesystem Root
/dev/nvme0n1p9
00927e71-7570-470f-9eb5-3af1d5247385
Linux Filesystem

MyDocuments
Partition 6
136 GB exFAT
136 GB — 86 GB free (36.8% full)
exFAT (version 1.0) — Mounted at /media/john/MyDocuments
/dev/nvme0n1p6
15FA-4139
Basic Data

MyChemistry
Partition 7
99 GB exFAT99 GB (99,321,115,136 bytes)
exFAT (version 1.0) — Not Mounted
/dev/nvme0n1p7
15FA-19C0
Basic Data

Filesystem
Partition 8
724 MB NTFS
724 MB (723,517,440 bytes)
NTFS — Not Mounted
E652D9CF52D9A519
Microsoft Windows Recovery Environment (System)

---

### Post by oldfred on 2022-09-22
Better to post actual code output with commands from terminal like 
sudo fdisk -lu
sudo gdisk -l /dev/sda
lsblk -f
cat /etc/fstab

How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

No real difference between SSD & HDD or with gpt.
With SSD you may want noatime with SSD.

My fstab, note nothing refers to SSD (other than noatime) nor gpt.
But with gpt you do have an additional partition option as you can use partUUID. Most use UUID, or label. Using device like /dev/sda, not recommended.

```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/**[/COLOR][COLOR=#000000]$ cat /etc/fstab [/COLOR]
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/nvme0n1p3 during installation 
UUID=3c01cc90-636c-4a7e-aa12-fe610d95d5f3 /               ext4    noatime,errors=remount-ro 0       1 
# /boot/efi was on /dev/nvme0n1p1 during installation 
UUID=138A-44FF  /boot/efi       vfat    defaults      0       1 
# swap was on /dev/nvme0n1p2 during installation 
UUID=393cd3f4-c4d8-42df-bae3-4690f542ee0b none            swap    sw              0       0 
# Entry for /dev/nvme0n1p5 on z690: 
UUID=012965c6-d942-4efb-8e1d-5dcc54911f3a /mnt/data ext4 noatime 0 2 
# Entry for /dev/nvme0n1p6 on z690: 
UUID=cf40f922-78bb-4f82-93be-9c3720132a0d  /mnt/photos    ext4  noatime  0  2 
tmpfs /tmp tmpfs noatime,nodev,noexec,nosuid,mode=1777 0 0

[/FONT]
```

Good examples:
[https://wiki.archlinux.org/index.php/fstab](https://wiki.archlinux.org/index.php/fstab)
Many are older and ext4 is now used, not ext3 for example
[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)

---

### Post by cigtoxdoc on 2022-09-23
Thank you, oldfred.  The exFAT partitions are the most critical to add to the fstab. So for MyDocumentd then:
UUID=15FA-4139 512 exfat ? ?

So what parameters go after the UUID for exFAT partitions?

By the way, the use of exFAT partitions allows me to access the same files to make documents for those who want to see my output as PPTX, DOCX, and real ADOBE PDF as well as those who don't care if I use LibreOffice and StudioPro 2022 for PDF files.

John

---

### Post by TheFu on 2022-09-23
exFAT is best used for USB flash storage, if you have to share with non-Linux OSes.

For SSDs and spinning HDDs, use NTFS if you absolutely must physically connect the storage to other OSes.  NTFS is a modern, journal'd file system. That's a good thing, though it isn't as good as using a native Linux file system like ext4 or one of the Unix file systems like ZFS, xfs, f2fs and a few others, depending on the purpose.

If sharing data over the network is the only way that other OSes will access the data, choose a Linux/Unix file system and let the network protocol do the translation. That would be either NFS (or any Unix-like OS) or CIFS/Samba for MS-Windows.  These should be used only on the same LAN. Over the internet, choose something like scp or sftp.

BTW, GPT partitioning means ZERO to the fstab settings.  The exact same lines would be used with MBR/MSDOS partition tables.

For non-Linux, non-Unix file systems the mount options are the only way to set permissions.  That means for NTFS or FAT-whatever file systems, we have to provide the owner, group, and permissions we want for all files and directories in the mount command.

So, the way I'd mount exfat is with this command:

```
sudo mount -t exfat LABEL=My_ExFAT   /data/junk  \
      -o dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002
```
 
That converts to an fstab line of:
```
LABEL=My_ExFAT   /data/junk   exfat  dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0
```
All on 1 line.  Of you want more details, there are manpages for mount.exfat, mount, and fstab which explain all the options.  Also, no spaces are allowed in the "options" section of the fstab.  There are 6 fields in the fstab. A space (or multiple spaces) separate those fields.  The last two fields - 0   0 - control backups and when fsck processing happens. For foreign file systems like exfat, they don't apply and 0 0 is the correct entries.  The fstab manpage explains more.

I prefer using the LABEL over using UUID or partition devices, since we humans get to make up the LABEL (use gparted) and can ensure it is unique for all storage in our collection.  Don't let the label have any spaces or special characters when you create it.

Write that line to the fstab file, then run
```
sudo mount -a
```

---

### Post by MAFoElffen on 2022-09-23
I have some questions from what you have posted, you are asking about, and seems to be causing confusion...
```

MyDocuments
Partition 6
136 GB [COLOR=#ff0000]exFAT[/COLOR]
136 GB &#8212; 86 GB free (36.8% full)
[COLOR=#ff0000]exFAT[/COLOR] (version 1.0) &#8212; Mounted at /media/john/MyDocuments
/dev/[COLOR=#ff0000]nvme[/COLOR]0n1p6
15FA-4139
Basic Data

MyChemistry
Partition 7
99 GB [COLOR=#ff0000]exFAT[/COLOR]99 GB (99,321,115,136 bytes)
[COLOR=#ff0000]exFAT[/COLOR] (version 1.0) &#8212; Not Mounted
/dev/[COLOR=#ff0000]nvme[/COLOR]0n1p7
15FA-19C0
Basic Data

```
- I am assuming these are the partitions that you want mounted in your fstab? Which now are being temporarily mounted to media...
(partitions #6 and #7 on NVMe device "nvme0n1") which for some reason, you formatted as ExFat.

In over 33 years of IT Consulting on Windows/Linux/UNIX/OSx, If I see NVMe and it's formatted as ExFAT, then I see something wrong...

Here is the more of the background story on that, so that you are informed, and know. ExFat came about (by Microsoft) to extend Fat32's filesystem beyond it's size limitations (partitions and filesize). It was originally meant for removable media, such as flash drives and SD Cards It was not meant for removable mass storage devices, nor internal drives. 

ExFAT, is normally created on a MSDOS partition table, which has a limitation of primary partitions (4), which is extended by virtual extended logical partitions. It can be created on a GPT partition table, to get around the primary partition number limit, but still has a limit of files per partition and size size limits (4GB)... 

I couldn't understand why I couldn't copy a copy a windows ISO (bigger than 4GB) to an empty 400GB flash drive... <<< The limitations of ExFAT was why.

Articles will tell you it is universally more accepted between OS'es like Windows, Linux, and OSx, but that is a big misnomer. They can read and write to ExFAT but... That is all. You need to install additional utilities to Linux and OSx to be able to format or check the integrity of ExFAT filesystems.

Although Linux will boot from ExFAT if a LIE (Live Image Environment) on most MBR/EFI x86 systems... If an OSx native x86 system, it has to be GPT partition table, then ExFAT, or it will not be recognized as a bootable drive.

NTFS is readable and writable by Linux and OSx. It can be created and maintained within Linux. It is more robust (as a filesystem) than ExFAT. I has things that ExFAT does not. It's limitations are far beyond ExFAT... It has been accepted years beyond ExFAT as universally excepted by Linux and OSx as a readable/writable filesystem.

If I need data accessible between differing Operating Systems (mixed Win and Linux), then NTFS is my first choice. If Linux/UNIX, then Ext4 is my first choice.

---

### Post by TheFu on 2022-09-23
MAFoElffen has good points.

I seldom use exFAT or any FAT, unless it is mandated by specific hardware AND I'm using USB/microSD flash storage.  If I'm only on Linux with that type of storage, I choose f2fs, which is native Linux, designed for flash.  None of the flash-specific file systems are journaled, to save writes.  Lots of writes are bad for flash longevity. 

NTFS is used only when non-Unix OSes will be physically connected to non-Flash storage - either SSD, NVMe or spinning rust (HDD).

Picking the correct file system is important for hardware longevity, features, capabilities, compatibility and performance.  If we pick native Linux file systems, the default options are generally excellent for performance.  Whereas for other, non-native, file systems, performance can be 30% less using the defaults - or worse, letting a GUI do it like any that mount storage using gvfs and place that storage under /media.  That is to be avoided for lots of reasons, but it can be convenient if you only need a few small files copied to/from the storage or perhaps to/from a portable tablet/phone device.  For longer term connections to the storage, setting the best performance options if non-native Linux file systems are used can make an important different.


But sometimes we are just in a hurry and want to get some storage mounted.  For that, this command should detect and mount the file system with enough options to make it usable for the current userid.
```
  # Non-native file systems - ntfs, exfat, fat32
  sudo mkdir /media/canon  # the mount point (i.e. empty directory must pre-exist
  sudo mount -t auto -o uid=$USER /dev/sdz1 /media/canon
 
  # When done
  sudo umount /media/canon
```

That is exactly the way I mount an SDHC card from a PnS camera.  Obviously, /dev/sdz1  will need to be the correct device for your storage, or use the LABEL= or UUID= methods.
```
  sudo mount -t auto -o uid=$USER LABEL=CANON /media/canon
# or
  sudo mount -t auto -o uid=$USER UUID=15FA-19C0   /media/canon
```
You get the idea.  Any of those 3 methods is interchangeable, device, LABEL, UUID.  Actually, there are a few more, but most home users wouldn't want those other methods.  It isn't like you know the PCIe slot, port, disk, partition, right?   
/dev/disk/by-path/pci-0000:0a:00.2-ata-4-part2 doesn't exactly roll off the tongue, but it would work ... at least on my systems.  I use LABEL. Much easier to remember.

Please report back when you have this working and if not, post the exact (*EXACT) line from your fstab.

---

### Post by MAFoElffen on 2022-09-23
I can see the other side of that also... I can see that you are or were "a student" somewhere...

When I went back to school, I was quickly made a "Student Tutor" and "Teaching Assistant". Most of the infrastructure was MS Windows. Going from school and home, I had two online data stores (One Drive, Google Drive, etc.) and carried a jump drive between school and home. At home, I was mostly Linux. At school was MS Windows. For projects, I had VM Virtual Disks on my Jump drive... 

That drive was GPT with NTFS...

---

### Post by cigtoxdoc on 2022-09-23
Thank you for your replies, but instead of criticizing what I am doing, how about some very straight forward help.  You have all the information you need?  I help other scientists when they post problems on boards similar to Ubuntuforums.

I regularly flip back and forth between Win 10 (11 in one case) and Ubuntu Unity 22.04 on three PCs.  For those who say there is no way to check the exFAT partitions, use DISK MANAGEMENT on the Windows side.

It is too bad that no one has made a business of writing custom fstab files.

John

---

### Post by MAFoElffen on 2022-09-23
I am sorry that you can not see the body language that is between the lines of what I wrote. There is a vast difference between a recommendation and of criticism. We all have experience and personal preferences. We do really care that you are taken care of, and that you know the whole story... I did not see any criticism towards you or what you are doing, just care & concerns.

TheFu and oldfred did give you information on adding fstab entries. If you search on TheFu's past posts on fstab entries, he has some very good explanations on how to do that, and what the options in that section mean.

From what you have presently, on adding your two ExFAT partitions... I would create two empty directories in your home folder called "MyDocuments" and "MyChemistry". (respectively) Then in your fstab, the file entries would be:
```

UUID=15FA-4139  /home/John/MyDocuments  exfat  dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0

UUID=15FA-19C0  /home/John/MyChemistry  exfat  dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0

```
Replacing UserName "John" with whatever the UserName is... You may have to adjust the UID & GID to your own... 

You can see that by:
```

grep 'John' /etc/passwd

```
The output is going to be something like this:
```

John:x:1000:1000:John Doe:/home/John/:/bin/bash

```
Where the first number is your UID (User ID) and the second is your GID (Group ID)...

Please remain open-minded and enjoy.

---

### Post by TheFu on 2022-09-23
> **cigtoxdoc said:**
>  It is too bad that no one has made a business of writing custom fstab files.

I can't speak for others, but it wouldn't be profitable.  There are tools, probably installed on your box already, that will do it, but the information needs to be provided.

Oldfred asked for specific commands to be run.  I didn't see those command and the output requested, so rather than criticize about that, we showed examples.  There is seldom a simple answer, though I did post 1 'get it done' command, which was against my better judgement.  That was the line with "mount -t auto".

What I saw in most of the posts was concern along with reason for that concern.

I have concern about mounting storage inside a single user's HOME directory too.  I've seen bad things happen when that was done, but it is your system, so do what you want and live with the outcomes. Perhaps nothing bad will happen?  Who knows?  There's at least 80 yrs of experience in these posts. Feel free to ignore it.

---

### Post by cigtoxdoc on 2022-09-23
Hello MAFoElfen.  The partitions are already populated and nemo shows them /media/john/MyDocuments and media/john/MyChemistry.  I have this working on three PCs and got the idea of using exFAT from this or similar forum.  Everything works as long as I remember to click on each partition as listed in the left pane of nemo right after login.  The only reason for modifying fstab besides making for smooth operation is to get SpiderOakOne backup service to recognize the partitions and backup the files they contain.  I have listed below what I think is the correct fstab

# /etc/fstab: static file system information for DELL 7720 Laptop.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p9 during installation
UUID=00927e71-7570-470f-9eb5-3af1d5247385 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p2 during installation
UUID=C60D-9EBB  /boot/efi       vfat    umask=0077      0       1
# /media/john/MyDocuments on /dev/nvme0n1p6
UUID=15FA-4139  /media/john/MyDocuments  exfat  dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0
# /media/john/MyChemistry on /dev/nvme0n1p7
UUID=15FA-19C0  /media/john/MyChemistry  exfat  dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0
/swapfile                                 none            swap    sw              0       0

---

### Post by cigtoxdoc on 2022-09-23
Thank you for your comments.  Based on information I have received from this forum, I have always put my data on partitions that do not contain the home directory.  Also, the idea on using exFAT came from this or similar forum.  Moreover, I checked synaptic for any tools related building fstab, and I could not find any.  There was such a tool on an earlier version of Ubuntu, but as I remember, it included other lines that referred to Loop or something like that.  

John

---

### Post by TheFu on 2022-09-23
gnome-disks

---

### Post by TheFu on 2022-09-23
Incorrect - at least as posted because you didn't use 'code tags', so it appears like the entries are on 2 lines.  
> **cigtoxdoc said:**
> 
```

UUID=15FA-4139  /media/john/MyDocuments  exfat  dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0

UUID=15FA-19C0  /media/john/MyChemistry  exfat  dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0

```

Since I added code tags to your post, it appears they are on a single line, but just to be certain, fstab entries must be on a single line.
```

UUID=15FA-4139  /media/john/MyDocuments  exfat dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0
# /media/john/MyChemistry on /dev/nvme0n1p7
UUID=15FA-19C0  /media/john/MyChemistry  exfat dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0

```
Also, the uid and gid numbers must be from your user on Linux.  Use the 'id' command to find the actual numbers needed.

To edit the fstab file, use 'sudoedit /etc/fstab' That's the safest way.

---

### Post by MAFoElffen on 2022-09-24
I think he meant <edited>
> **TheFu said:**
> To edit the fstab file, use 
```

sudo edit /etc/fstab

```
That's the safest way.

---

### Post by TheFu on 2022-09-24
No, I meant that the 'sudoedit' command should be used. It is the safest way to edit most, but not all, system files.
There are a few exceptions for the crontabs, suders and passwd files, but that's all I know about.  The main /etc/crontab should be edited using sudoedit.

Learn more 'man sudoedit'.

To the OP, since we live a few hours apart, why not join the one of the weekly ALE.org online meetups if you need more help? Someone would be happy to share a screen and walk you through things.

---

### Post by cigtoxdoc on 2022-10-04
Thank you to all who replied.  Correct fstab shown below:

# /etc/fstab: static file system information.                                                                                                                                
#                                                                                                                                                                            
# Use &apos;blkid&apos; to print the universally unique identifier for a                                                                                                               
# device; this may be used with UUID= as a more robust way to name devices                                                                                                   
# that works even if disks are added and removed. See fstab(5).                                                                                                              
#                                                                                                                                                                            
# <file system> <mount point>   <type>  <options>       <dump>  <pass>                                                                                                       
# / was on /dev/nvme0n1p9 during installation                                                                                                                                
UUID=00927e71-7570-470f-9eb5-3af1d5247385 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p2 during installation                                                                                                                        
UUID=C60D-9EBB  /boot/efi       vfat    umask=0077      0       1
# /media/john/Mydocuments on /dev/nvme0n1p6                                                                                                                                  
UUID=15FA-4139  /media/john/MyDocuments  exfat  dirsync,nodev,nosuid,noatime,async,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0
# /media/john/MyChemistry on /dev/nvme0n1p7                                                                                                                                  
UUID=15FA-19C0  /media/john/MyChemistry  exfat  dirsync,nodev,nosuid,noatime,async,uid=1000,gid=1009,fmask=0002,dmask=0002    0     0
/swapfile                                 none            swap    sw              0       0


I had to remove the windows_names and timeout from the original suggestion to make things woek.

John

---

