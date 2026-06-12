---
title: "Fresh install on new HDD to 14 (T) after running out of disk space on Quetzal HDD"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by Aaron_Davidson on 2014-11-18
Had Quetzal (server) running LAMP & Squid for a couple of years on an old Dell with a P4 era celeron and 20GB HDD.

Fell over cos HDD full - mostly updates (had auto-update on). Would't get beyond GRUB loader.

Tried all sorts of stuff to delete updates - no joy - lots of dependency messages especially libgc. Followed some post as last resort which left it even worse - bottom line is HDD OK but full.

Swapped in another HDD - 75GB and installed Tahr (Server - headless), LAMP, Squid...

Now here's the question:

**How to I mount the old disk if I connect it to the second IDE channel so I can copy stuff off it?**

If I try and boot with both connected (BIOS report both fine) - I get a kernel panic. Tried erasing the contents of root partition on the old disk but no joy - still goes to GRUB loaded if I have this as the sole primary drive (but no further)

I know the old HDD is OK, but what do I need to do to it to get it to appear so I can copy stuff from it?

I'm not exactly a noob but have been searching for days and don't know what to do.

Many thanks in advance to anyone who has the time to explain what I need to do - I appreciate it.

Aaron.

---

### Post by Bashing-om on 2014-11-18
Aaron_Davidson; Hi ! Welcome to the forum .

OK, 2 things pop to mind;
1) the 75GB hard drive, in bios have you reset the priority such that it is now the higher boot option ?
2) Is Grub installed to the MBR of that 75 GB drive ?

I would suggest that you boot up a desktop liveDVD(USB) and let's look at the hard disks to know what we are working with.
```

sudo fdisk -lu
sudo parted -l

```

Then from the liveDVD, we (RE-)install grub to what is seen as that 75GB drive.
Then from the 75GB drive mount the subject partition of the 20GB hard drive to copy off your data.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Aaron_Davidson on 2014-11-19
Thanks Bashing-om, 
Both disks have grub loader - 75GB boots fine alone, 20GB just gets to ubuntu loader screen, Kernel panic with both in.
Yep - have set new drive as primary boot drive in BIOS.
I thought it might mean a live CD or making the 20GB drive removable (via some usb adapter) so it can be mounted after booting from the 75GB.
As the former is relatively free (cost of CD/DVD) and I don't want to spend money if I can help it, I'll try this tonight.
I'm guessing it would be useful to have a live CD with the desktop version of exact same distro?
Fingers crossed!

---

### Post by Bashing-om on 2014-11-19
Aaron_Davidson; Hey;

Yeah, always a good thing to have on hand the liveDVD of the installed operating system(s); Never can tell what might happen. With good backups and a liveDVD one can fix anything that goes south in the install ( given time and effort ) .

Clarify in my mind; With both hard dives connected, and booting the 75 GB drive from bios, there is no problem.
When Booting up the 20 GB hard drive by any means the kernel panic occurs .

Given that situation, we are looking at inspecting 'fstab' and 'grub.cfg' on  the 20 GB drive and making required alterations . We can do this from either the primary (75 GB ) drive or a liveDVD. Just verify what the UUIDs of the related partitions are and perhaps (RE-)install grub to the 20 GB drive. Remains to be seen.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Aaron_Davidson on 2014-11-20
Took two evenings!

See what you mean about live cd. After connecting all 3 drives - the DVD to load the live DVD...

Ubuntu live desktop sees the old drive. Got to copy everything off it except mysql data because of permissions so want to pursue being able to boot into server with two disks and copy this too...

OK - those commands:

[FONT=courier new]===================================================================================
[/FONT][FONT=courier new]ubuntu@ubuntu:/$ sudo fdisk -lu[/FONT]


[FONT=courier new]Disk /dev/sda: 80.0 GB, 80000000000 bytes[/FONT]
[FONT=courier new]255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors[/FONT]
[FONT=courier new]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=courier new]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]Disk identifier: 0x0001b480[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=courier new]/dev/sda1   *        2048      499711      248832   83  Linux[/FONT]
[FONT=courier new]/dev/sda2          501758   156248063    77873153    5  Extended[/FONT]
[FONT=courier new]/dev/sda5          501760   156248063    77873152   8e  Linux LVM[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Disk /dev/sdb: 20.0 GB, 20020396032 bytes[/FONT]
[FONT=courier new]255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors[/FONT]
[FONT=courier new]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=courier new]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]Disk identifier: 0x000cfc05[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=courier new]/dev/sdb1   *        2048      499711      248832   83  Linux[/FONT]
[FONT=courier new]/dev/sdb2          501758    39100415    19299329    5  Extended[/FONT]
[FONT=courier new]/dev/sdb5          501760    39100415    19299328   8e  Linux LVM[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Disk /dev/mapper/farnham-root: 18.7 GB, 18685624320 bytes[/FONT]
[FONT=courier new]255 heads, 63 sectors/track, 2271 cylinders, total 36495360 sectors[/FONT]
[FONT=courier new]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=courier new]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]Disk identifier: 0x00000000[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Disk /dev/mapper/farnham-root doesn't contain a valid partition table[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Disk /dev/mapper/farnham-swap_1: 1073 MB, 1073741824 bytes[/FONT]
[FONT=courier new]255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors[/FONT]
[FONT=courier new]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=courier new]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=courier new]Disk identifier: 0x00000000[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Disk /dev/mapper/farnham-swap_1 doesn't contain a valid partition table
[/FONT][FONT=courier new]===================================================================================[/FONT][FONT=courier new]
[FONT=arial]
And:

[/FONT][/FONT][FONT=courier new]===================================================================================[/FONT][FONT=courier new][FONT=arial]
[/FONT][/FONT][FONT=courier new]ubuntu@ubuntu:/$ sudo parted -l[/FONT]
[FONT=courier new]Model: ATA WDC WD800BB-75JH (scsi)[/FONT]
[FONT=courier new]Disk /dev/sda: 80.0GB[/FONT]
[FONT=courier new]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=courier new]Partition Table: msdos[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Number  Start   End     Size    Type      File system  Flags[/FONT]
[FONT=courier new] 1      1049kB  256MB   255MB   primary   ext2         boot[/FONT]
[FONT=courier new] 2      257MB   80.0GB  79.7GB  extended[/FONT]
[FONT=courier new] 5      257MB   80.0GB  79.7GB  logical                lvm[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Model: ATA ST320413A (scsi)[/FONT]
[FONT=courier new]Disk /dev/sdb: 20.0GB[/FONT]
[FONT=courier new]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=courier new]Partition Table: msdos[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Number  Start   End     Size    Type      File system  Flags[/FONT]
[FONT=courier new] 1      1049kB  256MB   255MB   primary                boot[/FONT]
[FONT=courier new] 2      257MB   20.0GB  19.8GB  extended[/FONT]
[FONT=courier new] 5      257MB   20.0GB  19.8GB  logical                lvm[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Error: /dev/mapper/farnham-swap_1: unrecognised disk label                [/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Model: Linux device-mapper (linear) (dm)[/FONT]
[FONT=courier new]Disk /dev/mapper/farnham-root: 18.7GB[/FONT]
[FONT=courier new]Sector size (logical/physical): 512B/512B[/FONT]
[FONT=courier new]Partition Table: loop[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Number  Start  End     Size    File system  Flags[/FONT]
[FONT=courier new] 1      0.00B  18.7GB  18.7GB  ext4[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/FONT]
[FONT=courier new]has been opened read-only.[/FONT]
[FONT=courier new]Error: Can't have a partition outside the disk!                           
===================================================================================[/FONT]




[FONT=arial]Looks pretty messed up!

Re clarification It wont boot if both drives are installed - but booting into live CD obviously works.

How/where do I [/FONT][COLOR=#000000] inspect 'fstab' and 'grub.cfg ?

Thanks again - so much happier already!

[/COLOR]

---

### Post by Bashing-om on 2014-11-20
Aaron_Davidson; Well ......

The good news, we know where the problem lies ;
> 
Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Disk /dev/mapper/farnham-root doesn't contain a valid partition table


The bad news:
I know nothing about LVM - if it were standard MBR partitioning I know how to spare off that partition table, but, LVM I do not have a clue .. 

I suggest we await the notice of those who do have the experience in this realm.

[INDENT][INDENT]Another of those times
[INDENT][INDENT][INDENT][INDENT]I know nothing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Aaron_Davidson on 2014-11-20
Oh well, no big deal. Got what I really wanted - squid proxy config files and IP's

Closed!

---

### Post by Bashing-om on 2014-11-20
Aaron_Davidson; Ho Kay ;

As you wish;
If you desire to 'close' this Thread ->
You must mark this thread solved;

Doing so ->
aides others seeking after a solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

we do better next time

---

