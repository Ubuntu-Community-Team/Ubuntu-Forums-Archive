---
title: "Gparted &amp; Dual Boot Question"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by H_a_D_3_z on 2011-03-15
Hello guys, I've been trying to install Windows7 along side of Ubuntu 10.10, but trying to sort out the partitioning is a little difficult to figure out.

I have Ubuntu already installed
Here is the screen shot for you from Gparted.
[ATTACH]186211[/ATTACH]

I want to use the 72.15Gb unallocated space for Windows7, and I believe that that (Windows) needs to be on it's own partition.  I just can't figure out how to get it to its own partition.  And after that you can point me in the right direction for dual boot installation.

Help?

---

### Post by cbowman57 on 2011-03-15
Pretty sure that Win 7 requires the first partition (sda1).

If you still want to go through with it make sure that your grub.cfg & fstab are using UUID, shuffle with GParted and be prepared to reinstall grub from your liveCD.

When you reinstall grub it should take care of your dual boot.

---

### Post by kagerato on 2011-03-16
As I understand it, you can install Windows 7 to a logical partition.  However, the Win7 installer itself will not let you proceed unless a primary bootable partition exists for it to write the bootloader files to.

The Win7 installer also has other major issues with multiple drives.  (It various cases it confuses the drive order compared to the BIOS, and ends up trying to install the boot loader on the wrong disk.)

The easiest way to get past the installer without tricks is certainly to install 7 to /dev/sda1 as a primary active partition.  Microsoft has made other options more difficult, though not impossible.

Installing Windows first is always wise, because it is guaranteed to globber the drive master boot record.  It never gives you an option about this, and is honestly just a really bad citizen overall.  When you do the reverse (Linux then Windows), you'll need to either reinstall Grub to the MBR or configure the Windows boot loader (NTLDR in XP, BootMGR in 7) to chainload Grub.  The latter is not a fun task (compared to chaining into Windows, at least).

---

### Post by Dutch70 on 2011-03-16
> **H_a_D_3_z said:**
> Hello guys, I've been trying to install Windows7 along side of Ubuntu 10.10, but trying to sort out the partitioning is a little difficult to figure out.

I want to use the 72.15Gb unallocated space for Windows7, and I believe that that (Windows) needs to be on it's own partition.  I just can't figure out how to get it to its own partition.  And after that you can point me in the right direction for dual boot installation.

Help?

Windows is not going to like living in a logical partition even if it is possible. You probably don't want to start off that way. 

One possibility is to shrink sda2 down to the size of your /home partition. You will be able to create a new primary partition once that is done, however I'm not sure windows will like living at that end of the hdd either. It would be best to move sda 2 all the way to the right. It will take a while to move 99GB. 

That should also join all of your unallocated space, so you can make a primary partition up to 80GB if you want, or you could move sda2 partially to the right and extend sda2 to give /home a little more room.(actually, extending it 1st would be best) You can try different scenario's just to get an idea what it will look like. Just click undo instead of apply, if you don't like it.

---

### Post by srs5694 on 2011-03-16
Windows does ***not*** require to be on the first partition (/dev/sda1), but it ***does*** require a primary partition (1-4). The order of the partition on the disk is unimportant, so installing to a partition that occupies the end of the disk is fine, so long as it's a primary partition.

Thus, the easiest and safest way to proceed is:


[list=1]
[*]Boot a Linux emergency disc.
[*]Launch GParted.
[*]Use GParted to shrink /dev/sda2 so that it ends immediately after /dev/sda5 rather than where it does now.
[*]In GParted, create a new primary NTFS or FAT partition in the free space.
[*]If you didn't do so after each of the preceding two steps, click the check-mark icon in GParted to apply your changes. If it complains that it couldn't fulfill all the constraints, try again, but fiddle with the "align to" option.
[*]Exit GParted.
[*]Open a Terminal window and type "sudo sfdisk -d /dev/sda > parts.txt"
[*]Copy parts.txt to a floppy disk, USB flash drive, CD-R, or some other removable medium.
[/list]


The last two steps constitute insurance. Under certain circumstances, the partitioning software in the Windows installer is known to misbehave itself rather badly and either convert logical partitions into primaries in ways that create illegel partition tables or delete logical partitions. The sfdisk command writes a backup of your current partition table to parts.txt, so you can easily recover if Windows does this (assuming you copy parts.txt to a removable disk). You can further increase your odds of success by not adjusting partitions in the Windows installer; just point it at the FAT or NTFS partition you create and tell it to install there, without creating any new partitions.

As others have said, you'll need to re-install GRUB when you're done. Using [Super GRUB 2 Disk](http://www.supergrubdisk.org/) should enable you to boot Linux so you can re-install GRUB by typing "sudo grub-install /dev/sda".

One more thing: You've got a tiny (2 MiB) NTFS partition at the end of the disk. Chances are this partition serves no purpose, but I can't be positive of that. I recommend you determine what it is and, if it's empty or holds files you know can be discarded, delete it from within GParted.

---

