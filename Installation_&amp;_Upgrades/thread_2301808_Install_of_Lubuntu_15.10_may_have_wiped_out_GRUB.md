---
title: "Install of Lubuntu 15.10 may have wiped out GRUB"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by Stuart Soloway on 2015-11-05
I have an old Acer Aspire laptop with 1GB of RAM.  I had Lubuntu 14.? running on it.  I tried to install Lubuntu 15.10 from a DVD, using the complete reformat and fresh install option.  (There was nothing worth saving on the disk).  It got to what I thought was the last stage of the install, displaying a box saying that my install was almost complete, and then it hung for hours.  I shut down (ungracefully -- I couldn't see an alternative) and powered-up, but all that would happen was that I would get a blank screen with a blinking text cursor in the upper-left corner.

I tried this twice, once giving it overnight to complete, with the same result.

I discovered I can get to BIOS on power-up; this was originally a Windows Vista machine.  But there is no indication there of GRUB existing -- I seem to remember that in the past I would see a pointer to it somewhere in the BIOS menues.  

I ran boot-repair (from the live disk) and it gave me a message to look at http:\\paste.ubuntu.com/13112323/ .  That file starts out with the following:

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 5751528 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error


Can anyone tell me what is going on and/or how to recover?

---

### Post by Bashing-om on 2015-11-05
Stuart Soloway; Hello;

Are you certain of the integrity of the .iso file ? Did you verify the md5sum ?
Are you certain of the burn to DVD ? Did you run the boot option " check disk for defects" ?

Once we have this as a firm foundation, we can then look at file system and Grub in particular.

[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by mörgæs on 2015-11-05
When this happens the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") is worth trying.

GRUB will be rebuilt automagically when you install again.

---

### Post by Stuart Soloway on 2015-11-05
The MD5SUM was correct.  I just checked it.

I always check "verify data" when I burn a disk, and I am sure I did it this time.

I am currently downloading the alternate ISO, but I'm open to other suggestions.  

Thanks.

Stu

---

### Post by Bashing-om on 2015-11-05
Stuart Soloway; HO Hay !

As the foundation is firm .. I would next:
look at the partitioning:
```

sudo fdisk -lu
sudo parted -l

```
And if these numbers are good ... I would - from the liveDVD (RE-)install grub .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by Stuart Soloway on 2015-11-05
Thanks, Bashing-om.  How do I reinstall GRUB?  It sounded from the other post that if I just reinstall Lubuntu from the alternate disk that should reinstall GRUB.  Is there a better way?

---

### Post by Stuart Soloway on 2015-11-05
Here's what I have.  I got an editor from parted complaining about sr0.  Could sr0 be the thumb-drive I had plugged in?  If not, is the error significant?  See below:

```
lubuntu@lubuntu:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 680.9 MiB, 713961472 bytes, 1394456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xac01f4bb

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1            2048 154224639 154222592 73.6G 83 Linux
/dev/sda2       154226686 156301311   2074626 1013M  5 Extended
/dev/sda5       154226688 156301311   2074624 1013M 82 Linux swap / Solaris


Disk /dev/zram0: 495.5 MiB, 519602176 bytes, 126856 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdb: 7.6 GiB, 8097103872 bytes, 15814656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00034c58

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15814655 15812608  7.6G  b W95 FAT32
lubuntu@lubuntu:~$ 


lubuntu@lubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54168 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  79.0GB  79.0GB  primary   ext4
 2      79.0GB  80.0GB  1062MB  extended
 5      79.0GB  80.0GB  1062MB  logical   linux-swap(v1)


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 8097MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8097MB  8096MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
Ignore/Cancel?
```

---

### Post by Bashing-om on 2015-11-05
Stuart Soloway; Hey ...

This is 'buntu, there are many ways and many paths to one end.
The means justifies the end.
In this case, my thought - confirm that the partitions are in order ... and if no fault is found ..
then. from the liveDVD one can mount the install root partition - MBR is all I am familiar with - and (RE-)install the boot code.
Once the partitions are verified . I will provide the commands - as required - to install the boot code.
IF it turns out from 'fdisk/parted' that what we have here is a UEFI issue, I would be stumbling to properly install the boot code.
However, with time and effort I bet we can make that happen.

I do not have access to a UEFI firmware based system, so not able to test/verify anything we do. IF your system is UEFI based .

And as to :
> 
It sounded from the other post that if I just reinstall Lubuntu from the alternate disk that should reinstall GRUB.


That too will get the job done, In cases of multiple issues, many times a new fresh install is the thing to do . Particularly so IF one is not confident in the consistency of the present install.

[INDENT][INDENT]there is no substitute for confidence
[/INDENT][/INDENT]

---

### Post by Stuart Soloway on 2015-11-06
I'm starting to think that something about my hard disk is fried.  I tried the following with the alternate install, running from a CD:

Check disk -- It complains about something like "Sr0 blkupdate request failure" with address 139992.  Then it goes on to check the cdrom drive, which is OK (but irrelevant).

Install -- I told it to reformat everything and create one ext4 partition.  It hangs for a  couple of hours saying "Partitions formatting", showing a 33% complete progress bar, and saying below that, "Creating ext4 file system for / in partition #1 of SCSI1 (0,0,0) (sda)..."

Rescue broken system -- A bunch of stuff scrolls by, including a complaint about Sr0 and the same sector as above.  Then it detects my keyboard, language, etc, and does other startup config stuff.  Finally, it asks me where to put the root directory.  If I choose sda1 or sda5 as my root file system, it says it can't mount it.  

All disks in the last 30 years or so have allowed a few bad sectors and provided a way to run without using them.  Why is the existence of a bad sector (if that is what is happening) sabotaging my entire hard drive?

Stu

---

### Post by Stuart Soloway on 2015-11-06
For what it is worth, I ran badblocks -s /dev/sda and it found none.

---

### Post by Bashing-om on 2015-11-06
Stuart Soloway; Welp;

I am confused as to why/how 'fdsik' sees and reports 16 instances of /dev/ramXX. Do not have a clue as to what is going on here .
As to the hard disk , the OS install looks good, just seems to me that all we need to do for the install is to install the boot code to the MBR of the hard drive. That much we can do from a liveDVD(USB) .

[INDENT][INDENT]maybe all there is to it ?
[/INDENT][/INDENT]

---

### Post by Stuart Soloway on 2015-11-07
Well, what I am going to say now will probably confuse you more:  I successfully did a clean boot (with formatting) of Lubuntu 14.04 from a CD.  It worked.  Then I did an upgrade to 15.10 from the same live DVD I have been using.  And that worked!  I was able to install a Canon printer and print a test page.  So it looks like the 15.10 reformatting and/or repartitioning of the disk did something funky.  

So my problem is solved.  But in the interest of the community I would be happy to report this as a bug, if that seems useful.  Do you know where to do that?

While your help didn't lead directly to the solution, I appreciate it, BashingOm.

Stu

---

### Post by Bashing-om on 2015-11-07
Stuart Soloway; Sure !

Great ya up and running.

If you think you have found a bug:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
And have the big boys check it out .

As the original matter is now concluded, however
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

solved by application of that 'nuclear' solution .
[INDENT][INDENT]that too
[INDENT][INDENT][INDENT]is a good thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2015-11-08
Thanks for marking the thread 'Solved'.

Before reporting bugs I suggest that you check the SMART data from your new install. If some local problem had a role in the play then there is less reason for reporting.

---

