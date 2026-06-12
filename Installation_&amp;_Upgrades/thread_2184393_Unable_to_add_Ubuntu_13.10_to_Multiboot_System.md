---
title: "Unable to add Ubuntu 13.10 to Multiboot System"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2013-10-28
I find that when I choose "something else" I am unable to see the unallocated space that I previously created for Ubuntu.  Only the main drives are listed (NTFS) and none of the smaller partitions can be seen.  Thanks in advance for any suggestions.

---

### Post by oldfred on 2013-10-29
Have you used all 4 primary partitions in MBR partitioning?

sudo fdisk -lu
  sudo parted /dev/sda unit s print

---

### Post by archp2009 on 2013-10-29
Thanks for the prompt reply.  Acronis Disk Manager is currently showing 2 primary partitions and 7 logical partitions on that drive.  If necessary I can use Grub Superdisk to get back the old Grub loader and possibly gain access to Linux Mint but then I will lose access to Windows 8. I have erased my old Ubuntu partition.  I had hoped that installing Ubuntu 13.1 where 13.04 used to be would create a new grub boot loader that would add Win8 to the list.  Does it matter whether or not the unallocated free space is the rightmost partition on the disk?  I shrunk the main partition and added Windows 8 before trying to add Ubuntu, so the unallocated free space is now in the middle somewhere rather than at the end.  If it will help to make the partition show up in Ubuntu, I can swallow up that free space into the Win8 (make the Win8 partition larger)and then shrink the same Win8 partition so that this free space is at the end rather than at the beginning.  I have never before had the problem of the Linux partitions not showing up during the installation of Ubuntu.  I did not see an option to upgrade either.

---

### Post by oldfred on 2013-10-29
Grub2's os-prober should still had Windows to menu, but you have to make sure the always hibernation or fast boot is off and that you have rebooted after a resize so it can run chkdsk. After any resize to a NTFS partition Windows has to run chkdsk.
If hibernation or chkdsk flags are set on NTFS partition then the Linux NTFS driver will not mount it.

---

### Post by archp2009 on 2013-10-29
Thanks again for your kind supporr.

From Live Disk

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d7d47e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    99474479    49736216    7  HPFS/NTFS/exFAT
/dev/sda2        99474487   287547434    94036474    7  HPFS/NTFS/exFAT
/dev/sda3       287547435   778204664   245328615    7  HPFS/NTFS/exFAT
/dev/sda4       778204665  1953520064   587657700    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x500b9b3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   203929110  1250258813   523164852    7  HPFS/NTFS/exFAT
/dev/sdb2           16065   203922244   101953090    f  W95 Ext'd (LBA)
/dev/sdb5           16128   203922244   101953058+   7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07510751

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       32127   466623989   233295931+   7  HPFS/NTFS/exFAT
/dev/sdc2       466624512   569534463    51454976    7  HPFS/NTFS/exFAT
/dev/sdc3       569536511   596211711    13337600+   f  W95 Ext'd (LBA)
/dev/sdc5       569536512   569927679      195584   83  Linux
/dev/sdc6       569929728   589459455     9764864   83  Linux
/dev/sdc7       589461504   593281023     1909760   83  Linux
/dev/sdc8       593281024   594257919      488448   83  Linux
/dev/sdc9       594259968   596211711      975872   82  Linux swap / Solaris
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x3319 of partition table 5 will be corrected by w(rite)

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x12ec12ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   240107489   120053713+   7  HPFS/NTFS/exFAT
/dev/sdd2       240091425   240107489        8032+   f  W95 Ext'd (LBA)
/dev/sdd5   ?   642637446   731883570    44623062+  15  Unknown

Disk /dev/sdf: 31.9 GB, 31914983424 bytes
255 heads, 63 sectors/track, 3880 cylinders, total 62333952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x46dd9c46

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            8192    62333951    31162880    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print 
Model: ATA ST31000340AS (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End          Size         Type     File system  Flags
 1      2048s       99474479s    99472432s    primary  ntfs         boot
 2      99474487s   287547434s   188072948s   primary  ntfs
 3      287547435s  778204664s   490657230s   primary  ntfs
 4      778204665s  1953520064s  1175315400s  primary  ntfs


You didn't comment regarding my question about putting the free space at the end of the disk. What do you think about the problem of my not seeing the unallocated space during installation attempt?

---

### Post by oldfred on 2013-10-29
You have some sort of partition table issue on sdc. That will cause issues until fixed.

 Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sdc > PTsdc.txt

               
 sudo fdisk /dev/sdc
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
q  # quit

---

### Post by archp2009 on 2013-10-29
Thanks again.  From Live disk:

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdc > PTsdc.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.ubuntu@ubuntu:~$ sudo fdisk /dev/sdc

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07510751

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       32127   466623989   233295931+   7  HPFS/NTFS/exFAT
/dev/sdc2       466624512   569534463    51454976    7  HPFS/NTFS/exFAT
/dev/sdc3       569536511   596211711    13337600+   f  W95 Ext'd (LBA)
/dev/sdc5       569536512   569927679      195584   83  Linux
/dev/sdc6       569929728   589459455     9764864   83  Linux
/dev/sdc7       589461504   593281023     1909760   83  Linux
/dev/sdc8       593281024   594257919      488448   83  Linux
/dev/sdc9       594259968   596211711      975872   82  Linux swap / Solaris

Command (m for help):

What now?

---

### Post by oldfred on 2013-10-29
It is not showing errors show you must w for write or the changes will not be saved.

Then in gparted or the installer you should see all your partitions. 
I suggest the manual install or Something else so you can install the grub2 boot loader to the same drive as the install. Then set BIOS to boot from that drive.

You have a lot of NTFS partitions. The Linux NTFS driver exposes all the hidden files that Windows like to hide. I suggest mounting Windows system partitions as read only and data partitions as read/write. Also if hibernated or needing chkdsk, the driver will not mount the partition until that flag is cleared to prevent damage that chkdsk or writing into the hibernated system may cause.

---

### Post by archp2009 on 2013-10-29
When you say, press "w to write changes," do you mean that one of those commands you gave me earlier made changes?  I should have mentioned earlier that Windows has been going crazy running chkdsk on all the drives.  I had it disabled because I was trying to do stuff with Windows 8.  I re-enabled autocheck and a few changes have been made.  I'm running another chkdsk on one of the disk that reported errors.  It is jammed full with movies and takes forever to do the chkdsk.  I don't understand what you mean by mounting Windows drives as read only, etc.

---

### Post by oldfred on 2013-10-29
If the fdisk command has run, you have to use w to save the changes.

       Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by archp2009 on 2013-10-30
Thanks again for the detailed information.  If the fdisk command has run, you have to use w to save the changes.


ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdc > PTsdc.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdc > PTsdc.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
ubuntu@ubuntu:~$ m
m: command not found
ubuntu@ubuntu:~$ sudo fdisk /dev/sdc

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
ubuntu@ubuntu:~$ 

I assume that If I restart the live disk that is the same as rebooting.

---

### Post by archp2009 on 2013-10-30
I repeated the fdisk commands from livedisk but firefox crashed and my quick reply evidently did not go through.  It said write failed and I had to reboot for the kernel to change.  I am now back into Windows.  It ran another chkdsk this time on the Vista partition.  I'm not sure what to do next in view of the write fail issue. (Sorry I see that my reply did go through, so what next?

---

### Post by oldfred on 2013-10-30
Was some partition on drive mounted? 

I might try testdisk and see what it says.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

            Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by archp2009 on 2013-10-30
Sorry, all this is beyond my level of Linux comprehension. I assume there is no simpler way to get Ubuntu 13.10 on there or you would have told me.  At what point in the course of installation do I do all this?  I have never heard of Morbius1.  Is this a program I can run from the live disk?  Which post in the section on ownership and permission of vfat/ntfs should I follow?

---

### Post by oldfred on 2013-10-30
If you look at that thread you will see he posted some relevant info. He is the user I am quoting so I like to give credit.

---

### Post by archp2009 on 2013-10-30
Testdisk generated a log that I was unable to attach or paste.  It said something about a partition being too small.  There is a very small partition at the beginning of the relevant 320gb disk.  I can't remember how it got there.  It is 15.69 mb of unallocated space.  I didn't want to delete it because I figured it would prevent booting.

---

### Post by oldfred on 2013-10-30
The issue seems to be partition 5 not one at beginning of drive.

---

### Post by archp2009 on 2013-10-31
> **oldfred said:**
> The issue seems to be partition 5 not one at beginning of drive.
Can you describe partition 5 so that I can identify it.  Could it be the data drive labeled as ext_hard_drive.  I could simply disconnect that one. That drive comes up as having a capacity of 114.49gb on Easeus Partition Manager, and yes, chkdsk takes forever to check files on it (all movies).  I used it for a couple of years as a remote drive.  I used to have it located in our crawl space below our living room tv and it is likely dusty inside. I think it's an IDE drive.

---

### Post by archp2009 on 2013-10-31
Two linux partitions (5 and 6) in the 329gb drive, with capacities of 1.865gb and 477 mb respectively, show up with triangles with exclamation marks in them in Easeus.  I don't know the significance of those symbols

---

### Post by archp2009 on 2013-10-31
Two linux partitions (5 and 6) in the 320gb drive, with capacities of 1.865gb and 477 mb respectively, show up with triangles with exclamation marks in them in Easeus.  I don't know the significance of those symbols.  Could it be that those two partitions are overlapping?

---

### Post by oldfred on 2013-10-31
From your post #5, It is a Linux formatted partition. 
But chkdsk on NTFS partitions may need running more than once as chkdsk does not fix everything on one pass.

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07510751

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       32127   466623989   233295931+   7  HPFS/NTFS/exFAT
/dev/sdc2       466624512   569534463    51454976    7  HPFS/NTFS/exFAT
/dev/sdc3       569536511   596211711    13337600+   f  W95 Ext'd (LBA)
[COLOR=#ff0000]/dev/sdc5       569536512   569927679      195584   83  Linux[/COLOR]
/dev/sdc6       569929728   589459455     9764864   83  Linux
/dev/sdc7       589461504   593281023     1909760   83  Linux
/dev/sdc8       593281024   594257919      488448   83  Linux
/dev/sdc9       594259968   596211711      975872   82  Linux swap / Solaris
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x3319 of partition table 5 will be corrected by w(rite)

---

### Post by archp2009 on 2013-10-31
ubuntu@ubuntu:~$ sudo fdisk -l -u /dev/sdb

Is it significant that partition table entries are not in disk order?

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x500b9b3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   203929110  1250258813   523164852    7  HPFS/NTFS/exFAT
/dev/sdb2           16065   203922244   101953090    f  W95 Ext'd (LBA)
/dev/sdb5           16128   203922244   101953058+   7  HPFS/NTFS/exFAT

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by oldfred on 2013-10-31
No, that is just saying sdb1 in your case is after the sdb2 partition. If you closely look at start sectors, you can see where each is on drive.

---

### Post by archp2009 on 2013-10-31
One irregularity, when I boot into XP and press F8 and select Safe Mode, the only option I get is to boot into I:/Windows. I wait forever and nothing happens.  When I load XP normally and open MY Computer, I: turns out to be a data disk.

---

### Post by oldfred on 2013-10-31
With Windows it may be which drive or what settings you have in boot.ini.

The red triangles in gparted say the partition has an issue and you can usually right click on icon and get more info. Not sure if Easus works the same or not. I use Linux tools for Linux. And usually suggest Windows tools for Windows, but sometimes the Linux tools may work for Windows.

---

### Post by archp2009 on 2013-10-31
Thanks for the tip on the boot.ini.  I was able to get into safe mode and did some runs of chkdsk from there.

Yes, right clicking enables viewing of the properties and contents of the partitions.  Under properties you see the type as well as the beginning and ending sector.  I notice that out of the nine partitions on that disk, only three pairs of adjacent partitions are contiguous; for example, partition 5 (ext3) ends at sector 593281023 and partition 6 (ext3) starts at 593281024 (the very next sector).  Partition 6 ends at 594257919 and Partition 7 (other) starts at 594259968 (not contiguous).  There are no missing sectors between partitions 5 and 6, or between 7 and 8.  There are two or three hundred or thousand missing sectors between partitions 1 (xp) and 2 (win8).  The same is true between partitions 3 and 4 and between 4 and 5 (linux).  I don't know if any of this has any significance. Easeus does not say anything in words to clarify why the triangles with exclamation marks are there just for 5 and 6.

---

### Post by oldfred on 2013-10-31
Partitions often are not adjacent. And in some cases space in between is required.
And all new systems use alignment on 1MB for better compatibility with new 4K drives and SSDs.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by archp2009 on 2013-11-01
So what can a Linux dummy do?

---

### Post by archp2009 on 2013-11-01
Why am I getting?
Can I write from live cd?

Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xbf7f of partition table 5 will be corrected by w(rite)

---

### Post by oldfred on 2013-11-01
I thought we fixed this back with posts #5 & 6??

Yes you should be able to use live installer.

---

### Post by archp2009 on 2013-11-01
Remember it was from live cd so a message came back saying "write failed." I have done this several times now and keep getting same result or on other occasions w command is not available at all. Sorry.

---

### Post by archp2009 on 2013-11-01
Trying again

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5d7d47e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    99474479    49736216    7  HPFS/NTFS/exFAT
/dev/sda2        99474487   287547434    94036474    7  HPFS/NTFS/exFAT
/dev/sda3       287547435   778204664   245328615    7  HPFS/NTFS/exFAT
/dev/sda4       778204665  1953520064   587657700    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x500b9b3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   203929110  1250258813   523164852    7  HPFS/NTFS/exFAT
/dev/sdb2           16065   203922244   101953090    f  W95 Ext'd (LBA)
/dev/sdb5           16128   203922244   101953058+   7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07510751

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       32127   466623989   233295931+   7  HPFS/NTFS/exFAT
/dev/sdc2       466624512   569534463    51454976    7  HPFS/NTFS/exFAT
/dev/sdc3       569536511   596211711    13337600+   f  W95 Ext'd (LBA)
/dev/sdc5       569536512   569927679      195584   83  Linux
/dev/sdc6       569929728   589459455     9764864   83  Linux
/dev/sdc7       589461504   593281023     1909760   83  Linux
/dev/sdc8       593281024   594257919      488448   83  Linux
/dev/sdc9       594259968   596211711      975872   82  Linux swap / Solaris
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xbf7f of partition table 5 will be corrected by w(rite)

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x12ec12ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   240107489   120053713+   7  HPFS/NTFS/exFAT
/dev/sdd2       240091425   240107489        8032+   f  W95 Ext'd (LBA)
/dev/sdd5   ?  1915651147  1641051896  2010184023   30  Unknown
ubuntu@ubuntu:~$ w
 19:47:39 up 7 min,  8 users,  load average: 1.09, 1.47, 0.87
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
ubuntu   tty2                      17:12    2:35m  0.08s  0.08s -bash
ubuntu   tty5                      17:12    2:35m  0.09s  0.09s -bash
ubuntu   tty4                      17:12    2:35m  0.10s  0.09s -bash
ubuntu   tty6                      17:12    2:35m  0.08s  0.08s -bash
ubuntu   tty3                      17:12    2:35m  0.08s  0.08s -bash
ubuntu   tty1                      17:12    2:35m  0.07s  0.07s -bash
ubuntu   pts/0    :0               19:47    3.00s  0.05s  0.00s w
ubuntu   tty7     :0               19:42    2:35m 22.92s  0.13s init --user
ubuntu@ubuntu:~$

---

### Post by archp2009 on 2013-11-01
Don't know if anything is happening or not

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdc > PTsdc.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sdc > PTsdc.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
ubuntu@ubuntu:~$ ?
?: command not found
ubuntu@ubuntu:~$ help
GNU bash, version 4.2.45(1)-release (i686-pc-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                            history [-c] [-d offset] [n] or hist>
 (( expression ))                        if COMMANDS; then COMMANDS; [ elif C>
 . filename [arguments]                  jobs [-lnprs] [jobspec ...] or jobs >
 :                                       kill [-s sigspec | -n signum | -sigs>
 [ arg... ]                              let arg [arg ...]
 [[ expression ]]                        local [option] name[=value] ...
 alias [-p] [name[=value] ... ]          logout [n]
 bg [job_spec ...]                       mapfile [-n count] [-O origin] [-s c>
 bind [-lpvsPVS] [-m keymap] [-f filen>  popd [-n] [+N | -N]
 break [n]                               printf [-v var] format [arguments]
 builtin [shell-builtin [arg ...]]       pushd [-n] [+N | -N | dir]
 caller [expr]                           pwd [-LP]
 case WORD in [PATTERN [| PATTERN]...)>  read [-ers] [-a array] [-d delim] [->
 cd [-L|[-P [-e]]] [dir]                 readarray [-n count] [-O origin] [-s>
 command [-pVv] command [arg ...]        readonly [-aAf] [name[=value] ...] o>
 compgen [-abcdefgjksuv] [-o option]  >  return [n]
 complete [-abcdefgjksuv] [-pr] [-DE] >  select NAME [in WORDS ... ;] do COMM>
 compopt [-o|+o option] [-DE] [name ..>  set [-abefhkmnptuvxBCHP] [-o option->
 continue [n]                            shift [n]
 coproc [NAME] command [redirections]    shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFgilrtux] [-p] [name[=va>  source filename [arguments]
 dirs [-clpv] [+N] [-N]                  suspend [-f]
 disown [-h] [-ar] [jobspec ...]         test [expr]
 echo [-neE] [arg ...]                   time [-p] pipeline
 enable [-a] [-dnps] [-f filename] [na>  times
 eval [arg ...]                          trap [-lp] [[arg] signal_spec ...]
 exec [-cl] [-a name] [command [argume>  true
 exit [n]                                type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or ex>  typeset [-aAfFgilrtux] [-p] name[=va>
 false                                   ulimit [-SHacdefilmnpqrstuvx] [limit>
 fc [-e ename] [-lnr] [first] [last] o>  umask [-p] [-S] [mode]
 fg [job_spec]                           unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMMAND>  unset [-f] [-v] [name ...]
 for (( exp1; exp2; exp3 )); do COMMAN>  until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or name >  variables - Names and meanings of so>
 getopts optstring name [arg]            wait [id]
 hash [-lr] [-p pathname] [-dt] [name >  while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]               { COMMANDS ; }
ubuntu@ubuntu:~$ w
 19:50:14 up 10 min,  9 users,  load average: 0.25, 0.95, 0.76
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
ubuntu   tty2                      17:12    2:38m  0.08s  0.08s -bash
ubuntu   tty5                      17:12    2:38m  0.09s  0.09s -bash
ubuntu   tty4                      17:12    2:38m  0.10s  0.09s -bash
ubuntu   tty6                      17:12    2:38m  0.08s  0.08s -bash
ubuntu   tty3                      17:12    2:38m  0.08s  0.08s -bash
ubuntu   tty1                      17:12    2:38m  0.07s  0.07s -bash
ubuntu   pts/0    :0               19:47    2:38   0.05s  0.05s bash
ubuntu   tty7     :0               19:42    2:38m 31.17s  0.13s init --user
ubuntu   pts/2    :0.0             19:49    6.00s  0.04s  0.00s w
ubuntu@ubuntu:~$

---

### Post by archp2009 on 2013-11-01
gparted still says sdc is unallocated

---

### Post by archp2009 on 2013-11-01
Why is it that I am unable to paste text here but I can post results from terminal in Ubuntu live cd?  Also the attach icon does not work for text files.

---

### Post by archp2009 on 2013-11-01
A program called GSmart Control indicates multiple uncorrectable read errors on the 320gb drive.  I don't know if it has any way to fix errors.

---

### Post by archp2009 on 2013-11-01
What about if I deleted all the linux partitions?

---

### Post by archp2009 on 2013-11-02
In my haste to get on with things I downloaded and used a program called Partition Table Doctor 3.5 which appears to be a crap program.  It involved writing an emergency floppy disk. I followed the suggestions for fixing the partition tables but it made all the Windows partitions inaccessible except Vista, and Vista can only be accessed by skipping one of the disk checks if I try to finish the chkdsks it hangs for one of them. I don't understand how to use the functions on the Partition Table Doctor floppy emergency disk.  I have all the data backed up on a usb hard drive using Acronis True Image 2014 but I have never tried recovering data with this drive and will only be able to use the recovery disk.  I have no idea whether or not the usb ports work when only a dvd is in use.  What do you suggest?

---

### Post by archp2009 on 2013-11-02
I went back to the PTD emergency disk and used their automatic recovery.  That really messed things up.  Can't use Acronis Recovery either now because it does not show the original Windows partitions as being allocated.  Where do you suggest I start to get my backups restored.  Will a Windows XP disk enable viewing and formatting of the original partitions?  Should I start by formatting the whole disk and restoring one OS at a time?

---

### Post by heir4c on 2013-11-02
I read this tread not in details but I see this at the end of /dev/sdc3:
```
 f W95 Ext'd (LBA)
```
So, you made the extended partition not with gParted but I think from in Windows (Windows use Dynamic Drives or something like that (to technical for me to explain) and that is not the same as gParted create a Extended partition. It gives troubles) you would have to recreate the Extended partition with gParted (and delete first all the Logic partitions and swap and the W95 Ext'd) and than create in the new Extended partition new Logic partitions.

---

### Post by archp2009 on 2013-11-03
Thanks very much.  On the face of it things look pretty hopeless. I don't know why I get so impatient.  I can't even see the xp32 disk now when I boot from xp disk.  I can see it from gparted but no partitions and new problems indicated besides unallocation.  Would you think that formatting is the only option.  The option to format seems to be there is GParted but I can't see the disk in Windows.  When I try to boot from the same disk as before it says bootmgr missing.  When I try to boot from the disk that Vista and Win7 are on I just get a black screen with scattereed colored squares.  Please suggest a next step for me to do.

---

### Post by oldfred on 2013-11-03
It looks like you are entering the w at bash or teminal not inside fdisk.

fred@fred-Precise:~$ sudo fdisk /dev/sda
[sudo] password for fred: 

Command (m for help): 


From fdisk you should get a command line and from there enter the fdisk commands.

---

### Post by archp2009 on 2013-11-03
Thank God for Live Disks!    I'm not sure what I didn't do before not to be inside fdisk. Here goes again... I thought we were doing sdc??

ubuntu@ubuntu:~$ sudo fdisk /dev/sda

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ 

I thought I had entered w.
Do I have to enter another command now?

ubuntu@ubuntu:~$ w
 20:18:30 up 8 min,  8 users,  load average: 0.29, 0.92, 0.70
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
ubuntu   tty5                      17:41    2:37m  0.08s  0.08s -bash
ubuntu   tty6                      17:41    2:37m  0.07s  0.07s -bash
ubuntu   tty2                      17:41    2:37m  0.09s  0.09s -bash
ubuntu   tty4                      17:41    2:37m  0.08s  0.08s -bash
ubuntu   tty3                      17:41    2:37m  0.08s  0.08s -bash
ubuntu   tty1                      17:41    2:37m  0.07s  0.07s -bash
ubuntu   pts/0    :0               20:16    6.00s  0.06s  0.00s w
ubuntu   tty7     :0               20:12    2:37m  9.16s  0.12s init --user
ubuntu@ubuntu:~$ 

everything says bash
now what?

---

### Post by oldfred on 2013-11-03
q to exit. See posts #6 & 7.
You want to do sdc. I was just posting an example from my system, & I did not want to use sdc.

---

### Post by archp2009 on 2013-11-03
I don't recall being asked for my password then.  Sorry I'm so illiterate in Linux.  
ubuntu@ubuntu:~$ sudo fdisk /dev/sdc

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk /dev/sdc

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk /dev/sdc

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ 

no password was requested

---

### Post by archp2009 on 2013-11-03
looking at dev/sdc gparted info: corrupted file $UpCase NTFs is inconsistent run chkdsk twice rebooting.  failed to mount /dev/sdc input/output error of ntfs is inconsistent no modification to ntfs was made by this software unable to read contents, etc. ntfs-3g

---

### Post by oldfred on 2013-11-03
From an Ubuntu liveCD/DVD/Flash you do not have a password. 

It seems that you need to run chkdsk from your XP install disk or any Windows repairCD. Often chkdsk does not fix everything on one pass so you may have to run it until there are no errors.
Linux NTFS driver will not mount a NTFS formatted partition that needs chkdsk to prevent further damage that chkdsk may not then be able to fix.

---

### Post by archp2009 on 2013-11-03
The problem is that when I run the XP install disk, it does not see (show) the correct harddisk labeled XP.  It wants me to install/repair  another one of my drives volume Backups. I don't know how to make the xp drive visible again.

---

### Post by oldfred on 2013-11-03
If it does not see it as a NTFS partition then it will not offer to run chkdsk. 
Did the write fix it show gparted and fdisk show a NTFS partition on sdc?

---

### Post by archp2009 on 2013-11-04
Eventually I found it based on size.  After 3 or 4 chkdsk's which took many hours it completed without errors, but the partition that was labelled Win8 did not show.  In fact none of the OS partitions showed up with their volume labels.  Some of the partitions reported unrecoverable errors as did the xp partition the first try.  I don't know if it would help to run a different windows disk.  Partition table doctor really did a job on messing up the whole system.  Is there a windows fix for mbr is missing error. I think that's what it says when I try to boot it as usual.  I am running chkdsk on C: now which the XP disk is seeing as Backups.

---

### Post by archp2009 on 2013-11-04
[COLOR=#000000]Did the write fix it show gparted and fdisk show a NTFS partition on sdc? Yes but with issues.  I can try it again later[/COLOR]

---

### Post by oldfred on 2013-11-04
If Windows does not see it at all there may be an issue with PBR or partition boot sector. Both partition table and PBR must also have valid NTFS boot data (even if data only partition).

If Windows does not see it run testdisk again.
       As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS.

---

### Post by archp2009 on 2013-11-04
Thanks.  I recovered the 320gb xp volume by using chkdsk repeatedly.  I am in the process of restoring my xp partition backup to that disk now.  Hopefully that will get me into at least one of the four Windows partitions.  I have been unable to view either of the other 3 Windows partitions.  I'm not sure if I can rememeber what disk I had Vista and Win7 on.  I know I had Win8 on the same physical disk as XP.  If the XP recovery works I will have a few options for viewing disks and partitions.

---

### Post by oldfred on 2013-11-04
Anyone with multiple installs especially on multiple drives should run this script. I actually made it part of my rsync backup just to always have a current list of installed systems. ( I have many and 4 drives, plus full installs on flash drives).

 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Boot-Repair and Supergrub also use above script. Boot-Repair adds more info also.
      
 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by archp2009 on 2013-11-05
The Acronis Image restore worked for around an hour (about 60%) and stopped, returning this message:  "failed to read from sector 0 of hard disk 1.  Try to repeat the operation.  If the error persists check the disk using CHKDSK."  At what point should we begin to think that the hard drive is ready for the sledge hammer/garbage compactor?

---

### Post by oldfred on 2013-11-05
From any Ubuntu go to disks or disk utility (named changed with versions), and click on drive and see what Smart Status shows. It can run lots of tests but all I know is passed is good and anything else is a new drive.

---

### Post by archp2009 on 2013-11-05
It showed the disk was ok on all tests.  I did another chkdsk /r/f and am trying the Acronis restore another time.

---

### Post by archp2009 on 2013-11-06
Acronis still had issues needing drivers, etc., i another disk, which I knew nothing about  I decided to write zeros through the XP partition and reinstall XP clean.  I have just realized that the XP  is installed on drive D: not on C:  Is that going to be manageable?

---

### Post by oldfred on 2013-11-06
Windows only boots from one primary partition. In Linux we see that as the boot flag. In Windows it is the active partition. And second installs always move boot files to active partition, so they do not have boot files to boot from.

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by archp2009 on 2013-11-06
Thanks so much for your patience with me.  My plan is to re-install the four Windows Operating systems from oldest to newest (XP-Vista-Win7-Win8) and lastly Linux because it is the only friendly one that doesn't set out to prevent the booting of every other operating system in the entire world. Lovely people at M$  It would appear that my copy of Partition Table Doctor was rewritten to do something worse.   I have no idea why I want so many operating systems except that I like a little variety now and then.  Also, there is occasionally a program that works best in one of the 4 OS's.  That first link you posted is the nicest summary I have ever seen.  My brain is very tired tonight but I intend to study it fully tomorrow.  The second link is well worth reading too.  My question is, do I need to reinstall XP to get it showing up on drive C: rather than D?  I Googled the issue and most people seem to say I need to re-install.  I still haven't seen a sign of a volume name or visible partition or drive letter showing up for either of the other three Windows Partitions (Vista, Win 7 or Win 8.)  I seem to think that I had the former two on the 1tb drive, but I'm not sure.  Easeus Partition Manager may help when I get it installed.  It took me a couple  of years to get all the stuff installed.  There is no rush to get it back again.  I expect to be installing stuff for the better part of the winter!

---

### Post by archp2009 on 2013-11-19
Hello again.  I have finally re-installed the four Windows operating systems. I just started to Install Linux Mint 15.  A couple of new things happened.  First I was asked if I wanted to dismount all the disks.  I clicked yes.  I had previously shrunk one of the drives to create 25gb of space for Mint.  When I entered the partitioning part of the installation I created a 15gb root partition and then a 5gb swap.  I finally tried to add the rest of the space as a home partition but there was no response when I clicked the + button.  I noticed another button to create new partition table.  I don't recall having to select that option before.   Because I wasn't sure what I was doing I reverted the changes but would like to try again but I'm not sure why I couldn't add the home partition.  Any help would be appreciated.

---

### Post by oldfred on 2013-11-19
I prefer to partition in advance as gparted seems to have a bit more flexibility and I can see what is going on better. But installer should work. 
I usually use gparted from live installer but often download both gparte & parted magic live CDs also. I use grub to directly boot ISO so it is easy for me to boot any new ISO from another hard drive or flash drive.

 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

You still have to use Something else or manual install but then just choose an existing partition.

---

### Post by archp2009 on 2013-11-19
I think it is going to be a steeper learning curve for me to partition prior to installation than inside the installer.  I tried it a few more times, including using different parts of the disk to create my unallocated space. Each time after creating two partitions inside the installer, I'm left with a third portion that reads as unusable.  Do I have to click "create new partition table?"

---

### Post by archp2009 on 2013-11-19
I had to merge two partitions on the drive so that the total number of partitions was 2 instead of 3.  The only problem was that Grub did not see Vista.  Actually, I had two Vista installations (32bit and 64bit) and neither of them was listed on the boot menu.  Is there a way to manually add the other installations to the list?

---

### Post by archp2009 on 2013-11-19
Actually, when I click on Windows 8 it takes me to the original Windows boot menu that includes the two Vista installations.  Thanks.

---

### Post by oldfred on 2013-11-19
All Windows boot files are in the one partition with the boot flag. Grub cannot find the other installs as they do not have boot files. Do not ever delete your Windows partition with the boot files without repairing the other installs first. And only partitions that are primary can be directly booted.
See link in Post #59 on how Windows works for multi-boot.

---

### Post by archp2009 on 2013-11-20
Thanks for the reply.  I realize that the MBR is at the beginning of the XP drive.  All the Windows partitions were primary.  There was one Data partition that was primary and I just changed it to logical. I know that deleting a Windows partition would make the computer unbootable.  The Mint root partition is primary and the swap and home partitions are logical.  When I boot my computer now it comes up with Mint at the top followed by XP, Win8 and Win7.  The XP fails to boot with a message about some missing files (forget the names). The Win8 and Win7 take me to the original boot loader set up by Win 8 which lists all 5 installations all of which still boot directly as far as I know.  If it is ok I will probably use Grub customizer to delete all but the Win8 entry and rename that one to simply "Windows Menu."  If I were to install Ubuntu 13.10 now, what do you think I would end up with as far as a final bootloader is concerned?  Should I leave well enough alone?

---

### Post by archp2009 on 2013-11-20
The single missing file that XP says is missing when booted from Grub is ntoskrnl.exe and it asks to reinstall that file.  When i boot from the MBR menu the XP loads normally.

---

### Post by oldfred on 2013-11-20
No idea what Windows has done in installing boot files when you have so many installs. Sometimes error messages are not what is really missing. Or it could be that PBR needs updating. Partition boot sectors need to be different for XP and newer if directly booting. 
When I ran a Windows 7 chkdsk on my XP install (actually did more fixes), but it converted to Windows 7 PBR and wanted to boot with bootmgr not ntldr. So I had to reset PBR with bootsec.exe in Windows.

Grub2's os-prober looks for Windows boot files and adds boot entries for those partitions with those boot files. If only one partition then that is all it will show.

 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by archp2009 on 2013-12-07
Hello again,

I would like to add a post for help regarding recovering my boot loader after making a change with Daniel Richter's grub customizer.  Can you point me to or move this post to the appropriate section.  I am currently unable to boot after adding an image using grub customizer.  All that happens is a black screen appears and hard drive activity ceases.  I tried using Rescatux/Grub 2 super disk without success.  I don't know if the Mint Live CD can help.  Thanks in advance for any further assistance.

---

### Post by oldfred on 2013-12-07
I have stopped recommending grub customizer. It makes many changes to grub and then that can cause issues.
If you need more than a few basic changes it is better to manually change grub, then you understand it better, but it does then have a bit of a learning curve.

You may have to totally uninstall grub2 & reinstall it to get grub back to where it was.
You should be able to use Boot-Repair.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by archp2009 on 2013-12-08
I found out that it is possible to install grub customizer from the Live CD,  Then it's just a matter of selecting the Linux boot partition and all of the options of the Customizer are available again.  I just had to delete that image and I was back to my original boot loader.  I still don't know why the image didn't work, though.  The author told me in a question previously that there are issues with large fonts and I do use large fonts.  I can understand why you would not recommend this software, though.  It definitely has a few bugs, but then again, as we have seen, so does Grub2.  Putting the two of them together seems to multiply the likelihood of what seem like fatal bugs.  The author has to spend so much time dealing with reports of bugs that he probably doesn't have enough time to spend improving the software. Seems like a premature release IMHO.

---

