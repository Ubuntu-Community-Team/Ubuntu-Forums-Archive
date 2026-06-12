---
title: "Ubuntu 12.04 installer cannot recognize Windows 7 partitions in a Hybrid hard drive"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by i2000s on 2013-07-05
I am trying to install a dual-boot system with 12.04. However, when I run the LiveCD in a bootable USB stick, I only get as far as the "Install" window where you can select the partitions for your drives. I do not have the "Install Ubuntu alongside with Windows 7" option which is usually seen for Windows 7 users. I choose "something else" option to try to find my free space to install Ubuntu 12.04. However, on the bottom where it says "device for boot loader installation" I have "/dev/sda" only and cannot select any partition. I realize that the installer cannot recognize my hard drive partitions at all! 

All the options to change the drives are greyed out, most likely because there are no drives in the window. I checked the property of partitions within Windows, only two primary partitions are assigned. I have C, D, E, F, G and a system reserved partition. They are all "basic". Nothing indicate there is a dynamic partition. 

The installer does not recognize anything. When I go into an Ubuntu session and use the disk utility manager I can see the partitions in the disc, but if using Gparted, it shows the hard drive is unallocated. 

I've been over the forums many times, but all the answers I've found have not worked for me. I also tried run the os-prophers command in the "try ubuntu" liveCD booted ubuntu system. It can recognize that the Windows 7 was installed in the system. It just does not work on installation! 

I suspect if there is anything with my special Seagate Momentus XT hard drive. The hard drive is hybrid with 4G Flash hidden space, and all the rest is normal disc. I also found there are some Momentus XT hard drive users who cannot neither install dual-system on the hard drive. There are solutions on changing gpt to mbr and reinstall Windows after Ubuntu was installed. But I cannot do that, because I don't have large enough hard drive to backup my old disc, and I cannot affort the time to install every software I installed in Windows before. So far, I did not see any safe solutions. 

If you have any idea to do the dual installation, Please share your solutions here. Thanks in advance!

I reported this suspicious hardware problem here:
[http://ubuntuforums.org/showthread.php?t=2160192](http://ubuntuforums.org/showthread.php?t=2160192)

PS: report after this problem of installation has been solved: this problem turns out to be a problem of partitioning, may not related to the hardware. But this hybrid hard drive does cause considerable file-corruption problem as I have experienced after installing Ubuntu... Hope this further problem related to this type of hard drive can be solved in the future.

---

### Post by fantab on 2013-07-06
What computer do you have, laptop/desktop? What model and brand?

Post a screenshot of your HDD and its partitions from Windows and another from Gparted.
Boot with Ubuntu LiveCD and run the following in Terminal:
```
sudo parted -l
```
and post its output here.

Also check in your BIOS for HDD SATA Mode and tell us what mode it is set in.
Is there an UEFI boot in the picture? How does windows boot, legacy mode or Uefi?

---

### Post by i2000s on 2013-07-06
I am using ThinkPad X200 tablet laptop computer. The HDD is PATA-SATA Momentus XT 500G with firmware SD28. A snap shoot of the HDD in Windows 7 can be found here:
[http://www.flickr.com/photos/52606482@N08/9221664889/]("http://www.flickr.com/photos/52606482@N08/9221664889/")

I will run liveUSB shortly.

---

### Post by i2000s on 2013-07-06
I checked the BIOS HDD SATA mode, it is AHCI mode. I don't know how to verify the Windows boot mode (legacy/UEFI?). Is there any way to check it?

I checked the property of the disc, I got this:
[http://www.flickr.com/photos/52606482@N08/9225285708/]("http://www.flickr.com/photos/52606482@N08/9225285708/")
Since it is MBR, I assume it is booted by legacy MBR. 
Also, if following this wiki: [https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode]("https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode")
I can see that my USB stick is booted in non-UEFI mode.

My USB bootable flash doesn't work this time. It may be destroyed after I delete some files in order to remove the Fedora system installed in it. I will try the linux command later.

---

### Post by i2000s on 2013-07-06
In Ubuntu liveUSB mode, I got the following result (/dev/sdb is my flash disc):

> this@this:~$** sudo fdisk -l**

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x211e14cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   169191423    84492288    7  HPFS/NTFS/exFAT
/dev/sda3       489922560   674242559    92160000    7  HPFS/NTFS/exFAT
/dev/sda4       169191424   935641087   383224832    f  W95 Ext'd (LBA)
/dev/sda5       169193472   489922559   160364544    7  HPFS/NTFS/exFAT
/dev/sda6       674244608   850622463    88188928    7  HPFS/NTFS/exFAT
/dev/sda7       850624512   935641087    42508288    7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdb: 4030 MB, 4030726144 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7872512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad4ebea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7871849     3935893+   c  W95 FAT32 (LBA)
this@this:~$ **sudo parted -l**
Error: Can't have overlapping partitions.                                 

Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 4031MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4030MB  4030MB  primary  fat32        boot, lba

this@this:~$ **df -h**
Filesystem      Size  Used Avail Use% Mounted on
/cow            3.9G   40M  3.9G   2% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  872K  1.6G   1% /run
/dev/sdb1       3.8G  695M  3.1G  19% /cdrom
/dev/loop0      655M  655M     0 100% /rofs
tmpfs           3.9G   16K  3.9G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   76K  3.9G   1% /run/shm
/dev/sda2        81G   50G   32G  62% /media/3C3AFF5B3AFF111E
/dev/sda5       153G   74G   80G  48% /media/488BAB14A1412A95
/dev/sda3        88G   42G   47G  48% /media/E


---

### Post by fantab on 2013-07-06
> $ **sudo parted -l**
Error: Can't have overlapping partitions.                                 

The error suggests that this is a 'mis-sized extended partition' issue. This problem can be fixed with '[**FIXPARTS**]("http://www.rodsbooks.com/fixparts/")', which can be run from LiveUbuntu.
Now see what does 'sudo parted -l' has to say. Post the output. If there are no errors then proceed with Ubuntu installation. 

In case you still get errors even after running Fixparts then I am afraid you may have to Delete partitions D, E, F and G and recreate them accordingly.
Ubuntu needs atleast two partitions; one for '/' and another SWAP.

Try fixparts and tell us what happens.

---

### Post by i2000s on 2013-07-07
Not sure what do you mean. First of all, it seems fixpart only works for GPT partitions. But I don't think I have any GPT partitions. (Correct me if I misunderstand any point above. I just worry about whether I will lost my data.) Second, should I install the dependent package to use fixparts? I followed some post before to install gdisk which it said to be the package to enable fixparts. But I did not get it installed. 

Let me know if you can answer my question before I go to try soon... Thanks.

---

### Post by fantab on 2013-07-07
I don't thnk you have GPT, it does not need an Extended partition. If there is no GPT then UEFI can be ruled out.

In your case we'll use fixparts to fix the problem, if any, with Extended Partition. Read the fixparts link carefully. Since you will be using 'fixparts' from LiveDVD/USB its installation will be temporary, ie, it will be there only untill your shutdown. So let it install whatever it needs to install.

BACKUP ALL YOUR IMPORTANT DATA first. Its always a good idea to have Backups. Because managing partitions and installing new OS can go bad and result in Data Loss.

---

### Post by i2000s on 2013-07-07
Ok, I am seeking some extra disc to backup some of my data... Fingers crossed.

Read again the instruction, and then I will go to try soon... Thanks.

---

### Post by i2000s on 2013-07-07
Hi fabtab,

I tried to run fixparts in windows as it is available, but I got some sincere information:
[http://www.flickr.com/photos/52606482@N08/9226444595/]("http://www.flickr.com/photos/52606482@N08/9226444595/")
I pressed "P" under fixparts command to show the list above. As you can see, fixparts may omit the last two partitions. To my understanding, this will remove my last partitions. Am I right? However, I do not want to lose the partitions there. What should I do now? 

My plan is merging the last two partitions (F and G in Windows) into E using my Acronic disc management software, and then do the fixparts test again. Alternatively, since D is logical and E is primary, I can merge G into F, and do the fixparts test. Any other better way to do this fix without deleting data? Thanks.

---

### Post by fantab on 2013-07-07
Have run the necessary fix using fixparts? 

If I were you I would BackUP all my data on D, E, F and G. Then I would Delete all the Logical Partitions and the Extended Partition. Then I would recreate partitions the way I want them.
'msdos' partition table can have only 4 primary partitions. So I would have three Primary Partitions and would make my fourth as Extended Partition. And then would create Logical Partition as required within the Extended Partition.

However try and see how it works your way.

Good Luck...

---

### Post by i2000s on 2013-07-07
> **fantab said:**
> Have run the necessary fix using fixparts? 

If I were you I would BackUP all my data on D, E, F and G. Then I would Delete all the Logical Partitions and the Extended Partition. Then I would recreate partitions the way I want them.
'msdos' partition table can have only 4 primary partitions. So I would have three Primary Partitions and would make my fourth as Extended Partition. And then would create Logical Partition as required within the Extended Partition.

However try and see how it works your way.

Good Luck...

Some results of running fixparts were shown before your post. 

The problem for me is I don't have enough space to store any two or more partitions. I don't know if merging partitions will have the same effect as deleting and recreating partitions. I looked at the partition table, it seems /dev/sda4 overlaps all the rest logical partitions. I think you are right: I'd better backup all my data in the logical partitions (D-G) and recreate the logical table. I am not sure what is the /dev/sda4. Let me try to borrow a backup hard drive, have a try, and then report.

---

### Post by Mark Phelps on 2013-07-07
According to the Win7 Disk Management screen shot, you have two primary partitions, one extended partition, and a bunch of logical partitions inside the extended partition. 

Merging logical partitions inside the extended is not necessary because you can have any number of logical partitions you want inside the extended partition.

Since "F" and "G" are nearly full, merging them with "E" will consolidate the free space inside the three logical partitions into one. So that would give you more free space in the new "E" -- which you could then shrink down to make room for Ubuntu.

My own preference (learned the HARD way) is to use Windows partitioning tools to modify Windows filesystems, and use Linux partition tools to modify Linux filesystems.  Since you have no Linux filesystems on the drive, I would go with Windows tools.

You should download the Minitool Partition Wizard Boot CD, burn it to CD -- and boot from that.

ANY partitioning exercise runs the risk of losing data, so if it were ME, I would NOT do the partition merge -- since you appear to have no way to back off the contents of "F" and "G".

Instead, I would do the following:
1) Use the Backup feature in Win7 to create and burn a Win7 Repair CD.  This will come in handy later, should you need to restore or repair the Win7 boot loader from the dual-boot install.
2) Boot from the Minitool CD and shrink "D" down to make some room.
3) Reboot into Win7 to let it make any adjustments it needs to "D".
4) Reboot from the Minitool CD and move "E" to the left.  Reboot into Win7 ...
5) Do the same for "F"
6) Do the same for "G"

One that is all done, use Something Else in the installer to create partitions in the unallocated space inside the Extended partition.

IF this seems like a LOT of work -- it is.  But nothing is gained by rushing through partitioning to save time; instead, taking it slow and easy, and doing filesystem checks along the way, reduces the risk of data loss.

---

### Post by i2000s on 2013-07-07
Thanks Mark for your detailed steps. I have about 20G unallocated space at the end. So, install space for Ubuntu should not be a problem.

I just found this thread: [http://ubuntuforums.org/archive/index.php/t-1147450.html](http://ubuntuforums.org/archive/index.php/t-1147450.html)
I am just curious can I do similar trick to rewrite the partitioning table to fix this overlapping problem? For me, the /dev/sda4 is overlapping all the logical partition space, although I don't know what it is...

Here is what /dev/sda4 spanning:
> this@this:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x211e14cf

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS/exFAT
/dev/sda2 206848 169191423 84492288 7 HPFS/NTFS/exFAT
[COLOR="#0000CD"]/dev/sda3 489922560 674242559 92160000 7 HPFS/NTFS/exFAT[/COLOR]
[COLOR="#FF0000"]/dev/sda4 169191424 935641087 383224832 f W95 Ext'd (LBA)[/COLOR]
[COLOR="#0000CD"]/dev/sda5 169193472 489922559 160364544 7 HPFS/NTFS/exFAT[/COLOR]
/dev/sda6 674244608 850622463 88188928 7 HPFS/NTFS/exFAT
/dev/sda7 850624512 935641087 42508288 7 HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdb: 4030 MB, 4030726144 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7872512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad4ebea

Device Boot Start End Blocks Id System
/dev/sdb1 * 63 7871849 3935893+ c W95 FAT32 (LBA)
/dev/sda3 (looks like my E partition in Windows 7) and /dev/sda5 are also out of order, where /dev/sda3 is said to be a primary partition yet included in /dev/sda4 as an extended partition. Is this the problem? Can I manually turn /dev/sda3 into logical partition or do something else to readjust the partition table accordingly? Technically, I can turn E where all my programs are installed into a logical parition using the Acronis tool in Windows right now.

---

### Post by i2000s on 2013-07-07
Ok, I think I have found the key to solve this problem, and actually solving it without complicated operations. Here come the report.

I used Acronis to turn partition E from Primary partition to Logical partition, and rebooted my computer. (Tried also merging F and G before, but failed. It doesn't matter.) Now, I am using the bootable USB stick to run Ubuntu to check how it goes. Here I have

> this@this:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x211e14cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   169191423    84492288    7  HPFS/NTFS/exFAT
/dev/sda4       169191424   935641087   383224832    f  W95 Ext'd (LBA)
/dev/sda5       169193472   489922559   160364544    7  HPFS/NTFS/exFAT
/dev/sda6       489924608   674242559    92158976    7  HPFS/NTFS/exFAT
/dev/sda7       674244608   850622463    88188928    7  HPFS/NTFS/exFAT
/dev/sda8       850624512   935641087    42508288    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4030 MB, 4030726144 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7872512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad4ebea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7871849     3935893+   c  W95 FAT32 (LBA)
this@this:~$ sudo parted -l
Model: ATA ST95005620AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   86.6GB  86.5GB  primary   ntfs
 4      86.6GB  479GB   392GB   extended               lba
 5      86.6GB  251GB   164GB   logical   ntfs
 6      251GB   345GB   94.4GB  logical   ntfs
 7      345GB   436GB   90.3GB  logical   ntfs
 8      436GB   479GB   43.5GB  logical   ntfs


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 4031MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4030MB  4030MB  primary  fat32        boot, lba


Moreover, my Gparted tool can recognize all my Windows (NTFS) partitions with C and a system reserved partition as the only primary partitions! Although these partitions are not automatically mounted and the sound controller may not be working, I guess I can now install Ubuntu safely with the unallocated space in my disc. Let me continue, and report later...

---

### Post by i2000s on 2013-07-07
This is a report from Ubuntu 12.04 OS :) Ubuntu was successfully installed. Looks fine; my stylus of the tablet works; internet works. But here are some subtle problems I need to solve:

1. To Automatically mounting all partitions.
2. No sound in Ubuntu. To be fixed.
3. corruption of files known related to the hybrid hard drive. -- This is really bad in Linux! The cursor stops responding every few seconds. I can even hear the noise of "clicking" in the hard drive more frequent than in windows. I seldom have this kind of problem in Windows before.
4. Return booting control to Windows 7.
5. Software installing, and optimization of performance. 
6. Detect other problems.

Ok, in the sense of solving the problem of installing, this thread will be marked as CLOSED soon. I may post other threads for problems I cannot solve in the other time. Thanks for the helps from Fantab and Mark. I appreciate your patience! 

I wish my experience of solving this problem of installing Ubuntu in a probmatic hard drive and dual system can help other people with similar situation save their time! Go Ubuntu!

---

