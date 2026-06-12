---
title: "Help: Fresh install (new computer) / Migration"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by gstuart on 2008-06-07
Hello - Hello - this is a bit long, but to summarize, I *just* built a new computer (Intel 64-bit Core 2 Quad CPU, Intel motherboard, ...), that includes two - 750 GB SATA II hard drives.  I want to accomplish two things:

(1) Make sure that these new SATA drives are properly partitioned and mounted;

(2) I have my old (Ubuntu) boot / Ubuntu file system hard drive (an IDE HDD, from my old computer, that includes my /home/greg directory).  When I plugged this IDE drive into the IDE connector on the motherboard of my new and rebooted, the computer booted using this old drive, and even loaded my old session, including Claws (email), Nautilus with my old /home/greg/ and other directories, various other programs (Freeguide, ...) ... even my last Firefox session on my old machine!

However, I just want to temporarily access this drive (not boot from it), and transfer my old settings (/home/greg/) plus a few other config files, etc., to my new machine!

  ----------------------------------------

After assembling my new hardware, I booted from the DVD, and did a fresh install of Ubuntu 8.04 LTS (64-bit) from an .iso disk that I had burned, pretty much accepting the default options that were offered.

During the install, the two HDD were recognized / reported as

SCSI3 (0,0,0) (sda) - 750.2 GB ATA ST3750330AS
SCSI4 (0,0,0) (sdb) - 750.2 GB ATA ST3750330AS

When asked how I wanted to "Prepare Disk Space" I chose the Partition > "Guided - Use Entire disk (SCSI3)" option, rather them Manual (partition).

When I rebooted, this is what I had / did:

My /etc/fstab is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=91810551-9ccc-454b-9b40-6ed033dfc689 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d0c86d7f-c822-4714-8a71-8a1b2cd79722 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

When I went into Places (menu) > Computer > I saw icons for my CD/DVD burner, a SCSI Drive icon (for which no "Properties" were available when I right-clicked on this icon - unrecognized / unmounted?), and a Filesystem hard drive icon, that contained root (/) and included dierectories (e.g., /media, /etc, /home/greg, etc.) when I double-clicked it.

Next, following some online guides, I typed the following:

greg@victoria:/mnt$ ls
greg@victoria:/mnt$

greg@victoria:/mnt$ cd /media
greg@victoria:/media$ ls
cdrom  cdrom0

greg@victoria:/media$ sudo fdisk -lu

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d1f55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1441801619   720900778+  83  Linux
/dev/sda2      1441801620  1465144064    11671222+   5  Extended
/dev/sda5      1441801683  1465144064    11671191   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

greg@victoria:/media$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1f55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89748   720900778+  83  Linux
/dev/sda2           89749       91201    11671222+   5  Extended
/dev/sda5           89749       91201    11671191   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Noting the last line (above), following these instructions,

[http://ubuntuforums.org/showthread.php?t=806155&highlight=doesn%27t+contain+a+valid+partition+table](http://ubuntuforums.org/showthread.php?t=806155&highlight=doesn%27t+contain+a+valid+partition+table)

I proceeded as follows:

greg@victoria:/media$ sudo mkfs -t ext3 /dev/sdb

mke2fs 1.40.8 (13-Mar-2008)

/dev/sdb is entire device, not just one partition!

Proceed anyway? (y,n) y

Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
45793280 inodes, 183143646 blocks
9157182 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
5590 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000     done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 34 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

greg@victoria:/media$ sudo su
root@victoria:/media# mkdir /media/sdb
root@victoria:/media# su greg
greg@victoria:/media$ sudo mount /dev/sdb /media/sdb
greg@victoria:/media$ sudo chown -R greg /dev/sdb
greg@victoria:/media$ sudo chown -R greg /media/sdb
greg@victoria:/media$ ls
cdrom  cdrom0  sdb
greg@victoria:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2008-06-07 11:25 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-06-07 11:25 cdrom0
drwxr-xr-x 3 greg root 4096 2008-06-07 17:42 sdb

Now, in Places > Computer I have a new hard drive icon, sdb, that shows the used / free space, etc. when right-clicked (i.e., it appears to be properly mounted).

Just to be sure, I did this:

greg@victoria:/media$ sudo mount -a

So, my questions are: does this look "OK?"  Do I need to also have a sda drive icon present, that is mounted, so that when I right-click it, I can see the disk usage, properties, etc.?  

How can I temporarily mount my old boot (system) drive, and transfer my old files / settings?

(Parenthetically, I also have some other drives - legacy NTFS hard drives from an older Windows XP computer, that I want to archive ion the sdb drive.)

I am primarily intending the first SATA drive to be my system / working drive (personal files in /home/greg/), with the second reserved for backups (I was using rsnapshot - a rsync derivative) on my old computer ...).  I just remembered also that I like to record and process (edit) television shows, and I probably should have a partition on one of the drives, reserved for that?  

I'd like to get all of this this sorted out now, as I am at the very beginning of a fresh install on a new machine.  Thus, I can even start from scratch (fresh OS install, again) right now, if needed.

Thank you all so much in advance - very much appreciated!  Greg  :-)

---

