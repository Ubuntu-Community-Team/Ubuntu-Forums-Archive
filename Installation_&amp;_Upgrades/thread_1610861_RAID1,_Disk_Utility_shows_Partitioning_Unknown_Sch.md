---
title: "RAID1, Disk Utility shows: Partitioning: Unknown Scheme"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by hickimau on 2010-11-01
Hi Ubuntu community.
 
A newly created RAID1 Array appears to be disrupted. This is a Software RAID, built with the Disk Utility. Two SATA Disks, each of 2TB Capacity. The RAID was created on the running System, not during Installation. The Ubuntu System itself runs on a separate Disk.
 
Both Disks have Partition Type: "Linux RAID Partition"
The RAID Array took about 6 hours to build (initial sync), the resulting device /dev/md0 is mounted r/w at /media/bunker and seems to work correctly. However the "Disk Utility" shows incorrect values about the RAID. It says under "Partitioning: Unknown Scheme:", and shows inccorrect values in "Volumes". 
 
I attached a screenshot of this Screen. (Screenshot-Disk_Utility.png)
 
 
**Output from parted:**
[FONT=Courier New][SIZE=1]> parted -l[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]Model: ATA ST340014A (scsi)[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Disk /dev/sda: 40.0GB[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Partition Table: msdos[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]Number Start End Size Type File system Flags[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]1 1049kB 514MB 513MB primary ext3 boot[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]2 514MB 2563MB 2049MB primary linux-swap(v1)[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]3 2563MB 10.7GB 8096MB primary ext3[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]4 10.7GB 40.0GB 29.4GB primary ext3[/FONT][/SIZE]
 
[FONT=Courier New][SIZE=1]Model: ATA WDC WD20EARS-00M (scsi)[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]Disk /dev/sdb: 2000GB[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Partition Table: gpt[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]Number Start End Size File system Name Flags[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]1 17.4kB 2000GB 2000GB RAID: bunker raid[/FONT][/SIZE]
 
[FONT=Courier New][SIZE=1]Model: ATA WDC WD20EARS-00M (scsi)[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]Disk /dev/sdc: 2000GB[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Partition Table: gpt[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]Number Start End Size File system Name Flags[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]1 17.4kB 2000GB 2000GB RAID: bunker raid[/FONT][/SIZE]
 
[FONT=Courier New][SIZE=1]Model: Unknown (unknown)[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]Disk /dev/md0: 2000GB[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Sector size (logical/physical): 512B/512B[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Partition Table: loop[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]Number Start End Size File system Flags[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]1 0.00B 2000GB 2000GB ntfs[/FONT][/SIZE]
 

 
[SIZE=2]**output from mdadm:**[/SIZE]
[FONT=Courier New][SIZE=1]>mdadm --detail /dev/md0[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]/dev/md0:[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Version : 01.02[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Creation Time : Sun Oct 31 12:38:57 2010[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Raid Level : raid1[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Array Size : 1953514414 (1863.02 GiB 2000.40 GB)[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Used Dev Size : 3907028828 (3726.03 GiB 4000.80 GB)[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Raid Devices : 2[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Total Devices : 2[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Preferred Minor : 0[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Persistence : Superblock is persistent[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]Update Time : Mon Nov 1 10:29:21 2010[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]State : clean[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Active Devices : 2[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Working Devices : 2[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Failed Devices : 0[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Spare Devices : 0[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]Name : :bunker[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]UUID : 14727e62:c865a027:912026d6:0655d074[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]Events : 32[/FONT][/SIZE]
[FONT=Courier New][SIZE=1]Number Major Minor RaidDevice State[/SIZE][/FONT]
[SIZE=1][FONT=Courier New]0 8 33 0 active sync /dev/sdc1[/FONT][/SIZE]
[SIZE=1][FONT=Courier New]1 8 17 1 active sync /dev/sdb1[/FONT][/SIZE]
 
 
Can i ignore this? 
 
Many thanks in advance for your answers.

---

### Post by hickimau on 2010-11-02
bump. 
 
Anybody else has a similiar problem? any ideas? 
EVERY help welcome. 
 
Thanks in advance,
h

---

### Post by BakCompat on 2010-11-04
I am interested in a solution to this as I will likely be installing a system shortly with that same model hard drive in a software RAID1 config, not a hardware RAID1.

First thing I see is that you have the Western Digital WD20EA**R**S, not the WD20EA**D**S. This has been the source of a lot of confusion on the Internets. I see you have the drive formatted to 512 byte sectors, whereas the 'R' model is actually the newer Advanced Format drive which uses 4096 byte sectors or 4K sector size if you prefer. You'll take a big speed hit there alone. See [http://en.wikipedia.org/wiki/Advanced_Format]("http://en.wikipedia.org/wiki/Advanced_Format") for a bit of info on the format, or check computer tech websites for reviews and whatnot.

Another issue is that these drives don't support the TLER command used by many RAID chips. AFAIK, this is an issue when RAID is set up in hardware, but seems to be ok for the most part when set up in software RAID using a decent file system. The guys behind FreeNAS seemed to figure this out when pushing ZFS over 'weaker' formats. However, other issues arise with it and RAID. Check their forums if you're interested in that topic.

Now, the TLER issue *seems* to not be an issue for software RAID, so I don't think that's the case here. I think it's the spindle timeout on this model drive, which apparently parks its heads EVERY 8 seconds. Now, that's fine if you are going to have that box set up as a file server for home, where you might only use it during off-peak hours for copying music or videos or whatnot. But, if you are planning on doing some more intensive I/O, then you might re-examine your choice of this drive model, and instead go with the Blue or Black line from WD or a different brand altogether. The power savings feature of the drive (some 40% average) is good especially for leaving on permanently. I have seen some people writing that they have downloaded the WD Tools disc and used it to alter the firmware settings for the drive to increase the spindle park timing from 8s to 5m or so. They allege that this increases the lifespan of the drive. Considering the number of negative reviews and comments on NewEgg for these models just "failing" they may indeed be right, but time will have to tell on that one.

Alternatively, if you want proper RAID working, you might consider the actual RAID edition drives from WD, whcih have "RE" in the model name. Coincidentally, they are much pricier, especially in the 2TB range... something like $280 each or so? For my money, I'd rather get 2 green or black drives (5 year warranty) in a RAID1 fileserver.

Your needs may not match mine, so the intent could be different.

I do not yet have a couple of these available for a RAID install, so I can't replicate this or investigate it myself. I only have a single one in a SFF case that I will be doing a straight up install on and use probably for FTP/SAMBA/NFS only - you know, FreeNAS without the lame BSD in it. ;)

If nothing else, I would immediately wipe the array and recreate a new one with a file system other than NTFS.. something that is native to linux ya know. :)

---

### Post by hickimau on 2010-11-05
Many thanks for your answer. First of all - i did not spend any second thinking about Vendors/Models/Editions of the drives itself. i simply bought disks with the highest capacity available (2tb) and the lowest price/tb. -> WD20EARS, EUR 95 per disc.
 
I really like reading about all the details, Sector sizes, headparking, and so on - but do not use the results on this readings into my decisions. I simply try to avoid dataloss due to failing disks, thus RAID1 in software. 
 
The NTFS thing is important as well, because all client machines run MS products, producing funny file names, etc. I put Samba on the Fileserver for serving the Clients.
 
OK, back to the facts. The Server (and the RAID) is up since 4 days now. The incorrect values displayed in the Disk Tool saying 119GB for the first partition. In fact, there are no partitions - only one - the whole Disk. At the moment, i copied about 370GB of files onto the RAID. Everything works fine until now. 
 
Next step will be another reboot, checking if the incorrect values disappear or my files disappear or any other funny effects occur. ;)
 
Thanks again

---

### Post by BakCompat on 2010-11-05
I did a bit more searching on the WD20EARS model drive, as I have one in a single install and expect to build a box with two of them shortly.

So it seems that the firmware of the disk is actually lying to linux and telling it that it has a 512 byte sector size instead of a 4096 size. Well, for the windows world, that works, but for us guys who like to actual have things tell the truth, it doesn't work so well. On the WD forum, there are several threads actually requesting a firmware for the disks that will report the TRUE size for Linux, BSD, Solaris, etc... Now, I suspect it will take quite a bit of effort to get them to publish one, but we'll have to see...

Based on some other searches for WD20EARS on here, it seems that the message is probably ignorable, though don't take that as fact. I think what's happening is that the disk utils are basically out of date and don't have full support for newer disks, particularly those that are pushing to 2 and now 3TBs.

If I were you, I wouldn't put it into production just yet. I'd run it for a few weeks with non-critical data like movies or music copied from elsewhere and do some random file xfers to and from it... like ftp or samba shares.. Basically give it a chance to start putting data bits all across the drive in non-consecutive locations. Then, maybe do some cloning tests or raid tests to check integrity.

---

### Post by icestation on 2010-12-28
This is very interesting.  I have a similar configuration and EXACTLY the same problem.  I created an mdadm (software) based RAID10 array using 4 WD20EARS as follows:

1) I did NOT partition the disks
2) I made several passes at this, as the first time I saw the "corrupted" partition table in disk utility I assumed the array was bad and I zeroed the superblocks on all 4 disks and started over.
3) At one point during this rebuild I also used the disk utility to format the individual 2TB drives with no partition table (format drive)

So here are the steps I took on virgin WD20EARS:

1) sudo mdadm --create --verbose /dev/md0 --metadata 1.2 --level=10 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde
2) Opened the disk utility, and formated /dev/md0 with no partitions as an NTFS file system
3) Mounted it using the disk utility as "bliss"

I repeated this process after I started over, and I got the same result both times. The second time I then waited until the array was synced.  (8 Hours).  I then re-synced the array again (fat fingers), using the disk utility (8 hours).

The result was a disk icon on my desktop named bliss that showed a stack of disks (presumably a RAID array) and the first screen shot.

I captured the first screen shot during the first sync of the first attempt, the second time round was identical.  I then hibernated the system, but as often seems to happen on my UBUNTU machine (but not always, why is this?), the hibernate failed.

Fortunately I had preserved the settings of the array in /etc/msadm/msadm.conf as follows:

ARRAY /dev/md0 level=raid10 num-devices=4 metadata=01.02 name=ubuntu-server:0 UUID=c60eb2ea:6a911abf:75743422:12ffb49d

(which incidentally can be generated after you build the array by doing: sudo mdadm --detail --scan)

So when the system booted the array came back.  However, disk utility appears to have a problem reading the partition table of the array, or reading the master boot record or something, because I now get the second screen shot.   What is interesting is that DISK UTIL CREATED this table to begin with so now why it cannot read it is a puzzle.  Even MORE interesting,  these partition blocksize numbers are identical to the ones reported by hickimau with the exception of the first "Free" block due to the array size difference.  

As I said, the first time I saw this I wiped the array.  That was a mistake.  The array is just fine.  I determined this the second time by creating the following entry in /etc/fstab:

UUID=23559D7F45CD5191                /media/bliss    ntfs    rw,utf8  0   0

You could also use

/dev/md0                 /media/bliss    ntfs    rw,utf8  0   0

(best to mount partitions using the UUID, my dad used to say.  Use:  ls -l /dev/disk/by-uuid to get the UUID )

then creating the mount point /media/bliss  (which did not already exist for some reason) and doing

sudo mount -a

However the second screen shot persists even if I close and re-open disk util (disk util does not even report the mount of /dev/md0) , and now the disk icon on my desktop is only a single disk picture not a stacked set of disks.

**Here is the parted list:**

iceman@ubuntu-server:~$ sudo parted -l
[sudo] password for iceman: 
Model: ATA HDS722580VLAT20 (scsi)
Disk /dev/sda: 82.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  78.9GB  78.9GB  primary   ext4            boot
 2      78.9GB  82.3GB  3398MB  extended
 5      78.9GB  82.3GB  3398MB  logical   linux-swap(v1)


Error: /dev/sdb: unrecognised disk label                                  

Error: /dev/sdc: unrecognised disk label                                  

Error: /dev/sdd: unrecognised disk label                                  

Error: /dev/sde: unrecognised disk label                                  

Model: Linux Software RAID Array (md)
Disk /dev/md0: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4001GB  4001GB  ntfs


**Here is the report from mdadm:**

iceman@ubuntu-server:~$ sudo mdadm --detail /dev/md0
mdadm: metadata format 01.02 unknown, ignored.
/dev/md0:
        Version : 01.02
  Creation Time : Sun Dec 26 11:35:44 2010
     Raid Level : raid10
     Array Size : 3907028864 (3726.03 GiB 4000.80 GB)
  Used Dev Size : 3907028864 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Dec 28 07:30:23 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           Name : ubuntu-server:0  (local to host ubuntu-server)
           UUID : c60eb2ea:6a911abf:75743422:12ffb49d
         Events : 24

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde
iceman@ubuntu-server:~$


**Questions:**
[B][COLOR=SeaGreen]
[/COLOR][COLOR=Green]1) Does anyone know how to re-synchronize disk util so that it recognizes the file system in /dev/md0 correctly?  Perhaps this is an NTFS issue.

2) Does anyone know the exact mount command issued by disk util when it mounts the RAID array? (I want to get that spiffy stacked disk icon back)[/COLOR][/B]  

Thanks to hickimau for taking the time to document this issue.  Thanks to bakcompat for the info on 4096 chunks and head parking.  I saw that article too and I have been thinking about increasing the park interval too.

By the way I think the reason partd does not report on my WD20EARS is because I deliberately left out the partition table per the comments about mdadm's author's personal preferences in the RAID wiki:

[raid.wiki.kernel.org/index.php/Partition_Types]("http://raid.wiki.kernel.org/index.php/Partition_Types")

---

### Post by icestation on 2010-12-28
Supplemental, looks like the cluster sizes really are 4096
iceman@ubuntu-server:~$ sudo ntfsinfo -m /dev/md0
Volume Information 
    Name of device: /dev/md0
    Device state: 11
    Volume Name: bliss
    Volume State: 1
    Volume Version: 3.1
    Sector Size: 512
    Cluster Size: 4096
    Volume Size in Clusters: 976757215
MFT Information 
    MFT Record Size: 1024
    MFT Zone Multiplier: 1
    MFT Data Position: 24
    MFT Zone Start: 0
    MFT Zone End: 122094655
    MFT Zone Position: 4
    Current Position in First Data Zone: 122094655
    Current Position in Second Data Zone: 0
    LCN of Data Attribute for FILE_MFT: 4
    FILE_MFTMirr Size: 4
    LCN of Data Attribute for File_MFTMirr: 488378607
    Size of Attribute Definition Table: 2560
FILE_Bitmap Information 
    FILE_Bitmap MFT Record Number: 6
    State of FILE_Bitmap Inode: 0
    Length of Attribute List: 0
    Attribute List: (null)
    Number of Attached Extent Inodes: 0
FILE_Bitmap Data Attribute Information
    Decompressed Runlist: not done yet
    Base Inode: 6
    Attribute Types: not done yet
    Attribute Name Length: 0
    Attribute State: 3
    Attribute Allocated Size: 122097664
    Attribute Data Size: 122094656
    Attribute Initialized Size: 122094656
    Attribute Compressed Size: 0
    Compression Block Size: 0
    Compression Block Size Bits: 0
    Compression Block Clusters: 0
iceman@ubuntu-server:~$

---

### Post by icestation on 2010-12-30
I searched the bug reports, and this problem does not seem to be in Triage nor beyond, so I created a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/695611](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/695611)

---

