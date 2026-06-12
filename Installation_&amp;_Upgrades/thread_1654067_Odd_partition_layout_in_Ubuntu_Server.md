---
title: "Odd partition layout in Ubuntu Server"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by phptek on 2010-12-27
Hi folks,

While I am well-versed in the *use* of Linux, I've never really dabbled in installation/config having always had machines supplied with an O/S pre-installed (Mostly RH/Fedora/CentOS)

So I'm a little confused about the "correct" way in which to setup partitions and the like but appreciate there are many ways to skin a cat.

The machine is a custom Mini-ITX machine to be used as a single-use development webserver, SVN repo, HTPC and general home fileserver. It had x2 unformatted 1TB SATA drives and I successfully installed Ubuntu 10.10 server onto one of them.

I ran df -ah and noticed an unfamilliar partition/device list with a bunch of entries listed under "Filesystem" labelled as "proc" "fusectl" and "none" for 8 others in that column.

I'm used to seeing something like this (From CentOS)

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             141G  129G  5.1G  97% /
proc                     0     0     0   -  /proc
sysfs                    0     0     0   -  /sys
devpts                   0     0     0   -  /dev/pts
/dev/sda1              99M   18M   77M  19% /boot
tmpfs                1005M     0 1005M   0% /dev/shm
none                     0     0     0   -  /proc/sys/fs/binfmt_misc
sunrpc                   0     0     0   -  /var/lib/nfs/rpc_pipefs

But instead I see this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/HTPC-root  912G 853M 865G 1% /
proc                               0      0       0        -   /proc
none                              0      0       0        -   /sys
fusectl                            0      0       0        -   /sys/fs/fuse/connections
none                              0      0       0        -   /sys/kernel/debug
none                              0      0       0        -   /sys/kernel/security
none                              963M 268K 963M  1% /dev
none                              0      0       0        -   /dev/pts
none                              970M 0  970M       0%  /dev/shm
none                              970M 32K 970M     1%  /var/run
none                              970M 0  970M       0%  /var/lock

Does this look right?

This was created via the built-in "walkthru" partition manager, but have to admit I have no idea what I'm doing and created a single primary partition on drive 2 (sdb1) and 2 partitions on Drive 1 (sda1, sda2 I think) but using LVM which was the default  highlighted by the Ubuntu installer.

I'm happy to start from scratch again, but would love just a "default" partition set or to follow someone else's recipe.

Suggestions, recommendations welcome and thanks for reading.

---

### Post by tgalati4 on 2010-12-27
What does the following say?

sudo fdisk -l

As you know there is no correct way to set up a partition layout.  You could probably come up with 4 or 5 layouts that would work equally well.  As time goes on, you will discover some shortcoming that the current partitioning scheme won't allow.

For instance I have Linux Mint 6 on a partition (based on Intrepid I think).  If I make a new partition on the same drive to install Linux Mint 9 (which uses ext4) then my Minty6 can't read ext4--it's not built into the kernel.

So, write down all of the use cases that you can think of.  Then remember, the one that you didn't think of will bite you.

Using Logical Volume Manager (LVM) provides a lot of expandability and configuration, but can cause headaches when setting up static mounts on other machines for streaming or remote mounts for web development.  So you have to weigh the convenience that LVM provides with the possible headaches it can create.

Another example:  LVM creates a virtual swap if the kernel doesn't find a dedicated swap partition.  This is a good thing.  However, if you want to try out a LiveCD, it can't use the LVM swap.  It will only use a dedicated swap partition.  So put a small swap partition on every disk.  It's OK to have multiple swap partitions.  You never know when you have to pull a drive and put it in another machine.  The swap partition will always be there and your LiveCD will need it if you have to perform a massive data recovery session.

Regardless, 6 months from now you will know how well your partitioning scheme works.

---

### Post by phptek on 2010-12-28
@[tgalati4]("http://ubuntuforums.org/member.php?u=241895") thanks for the response.

Here is the o/p of fdisk -l, and I'm not sure it looks particularly healthy!

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007bc67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32      121602   976510977    5  Extended
/dev/sda5              32      121602   976510976   8e  Linux LVM

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e704

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832   83  Linux

Disk /dev/dm-0: 993.9 GB, 993945190400 bytes
255 heads, 63 sectors/track, 120840 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 5951 MB, 5951717376 bytes
255 heads, 63 sectors/track, 723 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

```

Bite that I didn't *manually *create these partitions (/dev/dm-0 & /dev/dm-1 for example) if I recall, because I though the Ubuntu installer was having probs with an unformatted *brand new) drive, I used GParted off a Knoppix live CD to create partition tables (MS-DOS), the swap and "general" partitions for sda and gparted for a single "general" partition on sdb. It was the Ubuntu installer and partition manager that I got to make the LVM setup.

So am I to understand there is no set criteria for partitioning in terms of there being no *requirement *for a boot, swap or extended partition? - It's pretty much up to the installer/installee (me) as you say to judge what my requirements are?

I guess my problem with this is I'm not  sure *how *my requirements translate into a partition setup.

I will be installing XBMC and I can the potential for a number of logs from Apache, and perhaps some partitioning on the second drive for media separation of some kind (??) plus the need for hardware swap on both drives as you suggest, but what about other types of partition that I probably don't know about (yet)?

This is a rackmount machine, not a desktop. I designed and specced it to sit in a cupboard with no KVM peripherals, and access it over SSH from a windows or other Linux desktop as well as from a NMT/TV setup (For home cinema).

Thanks a lot for bearing with me.
Russ

---

### Post by tgalati4 on 2010-12-28
For stagnant media storage (music & videos) you can get away with ext2.  For everything else ext3 or ext4 (perhaps slightly faster).

You need to use the partitioner that comes with the server version of 10.10--which I presume is cfdisk--a text-based partitioner.  Knoppix is fine, but using an older version of gparted can cause issues with ext4 and LVM.  

Having a / (root directory) associated with a partition (either ext2, ext3, ext4, reiserfs, xfs, zfs, etc) is the only mandatory linux requirement.  Everything else (swap, home, var, tmp, usr) is optional.  By not having separate partitions for those common directories, they are just put on the primary / (root) partition.

Swaps are useful as I mentioned before, so put small ones 1-6 GB on each drive.  Having a separate home partition is helpful for multiboot and some backup scenarios, but a headless, rack server doesn't really make sense.

Having a separate media partition called /Music or /Video (ext2) would normally be found at /media/Music or /media/Video.

The server kernel handles all of the system directories--they are both files and file systems, but you don't need to worry about them.  I don't see any advantage of creating a separate partition for fuse connections (user space file system--on-the-fly-directory-mounts) or /var.  Only in extreme cases would you see a benefit in moving /var to a separate partition. 

LVM was designed for desktop file system expandability.  For a server, you will set up your file system layout and leave it for several years--to serve a specific purpose.  Not that you can't use LVM, I just don't see the advantage for a headless server.

If I was setting up a home media server with 2 x 1 TB drives, I would set them up as follows:

Drive 1:

15GB ext4 / Primary boot of server 10.10
15GB ext4 unused (future upgrade/dual boot, perhaps 10.12)
2 GB /swap
700GB ext2 reserve for software RAID--I doubt a miniITX board has hardware RAID

Drive 2:

15GB ext4 unused (rsync mirror of / 10.10 server)
15GB ext4 unused (rsync mirror of updated server 10.12)
2GB /swap
700GB ext2 reserve for software RAID.  Needs to be the same size as 1st disk

Software RAID will give you faster read/write performance for copying/streaming media if you stripe them.  You can mirror them to give you 2x reliability at 1/2 the storage space.  The swap disks will combine to give you 4 GB of swap with whatever RAM your machine has.  The boot partitions give you backup so you can add GRUB entries to boot from either drive and either version of 10.10 or newer.  So that gives you 4 partitions to boot from, with RAID data performance.  Adjust the numbers as you see fit.

If you were clever, you could put the server on a USB flash drive to boot and use the entire 1 TB of each disk for /swap and media.  You would have to configure the server to run entirely in RAM and rsync (/var/log) snapshots to disk every so often to preserve logs.  That gets technical and fiddly.  So, I recommend keeping boot partitions instead.

---

### Post by phptek on 2010-12-28
@[tgalati4]("http://ubuntuforums.org/member.php?u=241895") thanks again for the response.

What you describe makes a lot of sense - I forgot the term "headless" though to describe my hardware setup - apologies.

So my last questions are basically:

1). What reason would I *not *use ext4 for the 700GB data/RAID partition(s)
2). Can I use fdisk/cfdisk to "fix" what I have (borked partition tables etc) and then re-install or something else?

Oh and FYI my Mini-ITX board does indeed ship with hardware RAID but only for M$ O/S's..which is odd...(It's an Intel DG45FC)

Thanks a lot once again,
Russ

---

### Post by phptek on 2010-12-28
...oh one last thing

I'm slightly confused about dirs vs partitions at the moment with regards to a /boot or /root partition. /boot is an O/S dir which is created in the primary "root" partition - right?

Can you clarify that at all?

Thanks.
Russ

---

### Post by tgalati4 on 2010-12-28
/ is called "the root directory".  /root is a personal directory for the administrator and contains log dumps for certain admin functions.  /boot is where the kernels live and where /boot/grub lives for managing boot configuration.

Partitions are simply chunks of the disk to hold stuff, with physical markers stored in the partition table.  The filesystem is what is formatted into each partition.  It consists of the format type fat32, ntfs, ext2 or 3 or 4 and the directories /, /usr, /boot, /var, etc.

I wouldn't use ext4 for media because it is optimized for lots of little files that are changing all of the time.  It also eats up space ~10%.  ext2 is fine for static data consisting of large files--like music or movies.

ext3 is ext2 with journaling and it uses up ~5% space.  If you put your server on an UPS, then you don't need to worry about journaling for static media files.  If you plan on using the media directories for something else, like video or music editing, then you might use ext3 or ext4.  It boils down to your requirements and use cases.

I agree that proprietary hardware RAID is a pain, but search around.  Sometimes you can do all the configuration you need by booting into RAID BIOS (Control-S) typically.  Once your RAID is defined in the RAID BIOS, it shows up under linux.  In the example above, you would select /dev/sda4 and /dev/sdb4 (the 4th partition of each drive) to make the RAID set.

For serving media--software RAID is quite acceptable.

---

### Post by phptek on 2011-01-01
Fantastic. It took me a few goes with Ubuntu's own partitioner, but I'm there.

I also added an additional 100Gb partition on sdb for backups from app-data on sda (DB backups mostly).

All looks good now.

Thanks so much for your help.

Regards and Happy New Year from sunny New Zealand.

---

