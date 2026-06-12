---
title: "Unable to install grub in (hd0) fatal error?"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by colinsr1187 on 2008-08-17
Hello,

I am trying to install Ubuntu 8.04 on an MSI Wind.  I am following the instructions on the triple boot wiki to the "T".  For some reason my Ubuntu installation gets the following screen at 94%:
Unable to install GRUB in (hd0).
Executing "grub install (hd0)" failed.
This is a fatal error.

I have tried multiple times, even tried again from scratch(reinstall XP, then partition, then OS X, finally Ubuntu) I have upgraded the HDD to 320GB.  Set aside 40GB for each OS.  Any ideas?  This is my first Linux install, so I have absolutely no clue.  I have found a few other threads regarding "managing flags" in the partitions, but nothing seems to work.

Thanks.
Colin

---

### Post by colinsr1187 on 2008-08-17
I read in another thread to type "sudo fdisk -1" in terminal.  Heres the results.

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

Of note, I only have 4 partitions...XP - OSX - Ubuntu - Shared Storage.  No swap drive.  Could this be the problem?

---

### Post by ajgreeny on 2008-08-17
It's** fdisk -l** (a lower case L not 1 as you used.)

---

### Post by colinsr1187 on 2008-08-17
Here is the correction:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b926d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5227    41985846    7  HPFS/NTFS
/dev/sda2   *        5228       10454    41985877+  af  Unknown
/dev/sda3           10455       15681    41985877+   7  HPFS/NTFS
/dev/sda4           15682       38913   186611040    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


Tried again to install using the LiveCD, no dice.
sda1 is xp, sda2 osx, sda3 ubuntu, and sda4 storage.

---

### Post by ajgreeny on 2008-08-17
Ubuntu needs to be on an ext3 partition, not an ntfs as your partitions are, though the installer should be able to sort that if you choose "Manual" at the partitioning stage.  Just make sure you get the right partition to install to sda3, if that's what you want, and let the installer do its thing.  You will need to set a small swap partiton as well as the main Ubuntu root (/) partition, however, but this is easy when you choose the manual option.

---

### Post by colinsr1187 on 2008-08-17
During installation I am choosing Manual partition, ext3, and /.  Should I choose these settings first in Gparted?

Is it possible to have 5 partitions?  XP, OSX, UBUNTU, Storage, and small Swap?  Or do I have to forego the shared storage and just have a swap drive?

---

### Post by caljohnsmith on 2008-08-17
> **colinsr1187 said:**
> During installation I am choosing Manual partition, ext3, and /.  Should I choose these settings first in Gparted?

Yes, you can use Gparted to format your partition to ext3 first if you want before running the installer if you like. The mount point / has no relevance in gparted since it deals only with partitions and not file systems.
> **colinsr1187 said:**
> 
Is it possible to have 5 partitions?  XP, OSX, UBUNTU, Storage, and small Swap?  Or do I have to forego the shared storage and just have a swap drive?

Yes, here's basically how it works:
[LIST]
[*]You can have up to four "primary" partitions on your HDD, and Windows should always use a primary partition
[*]If you want more partitions like you do, you can have 3 primary partitions, and make a fourth "extended" partition. An extended partition is merely a container for as many "logical" partitions as you want inside of it (I think the limit is 63 logical partitions).
[/LIST]
Therefore, you could create the following:
```
sda1 = primary = Win XP
sda2 = primary = OSX
sda3 = extended
  sda4 = logical = Ubuntu
  sda5 = logical = swap
  sda6 = logical = storage
```
So note that logical partitions sda4, sda5, and sda6 are actually contained "inside" extended partition sda3. That scenario should work for you.

---

### Post by colinsr1187 on 2008-08-17
Could the lack of a swap be the cause of the error installing GRUB?
I am going to reformat the drive as you advised and try to reinstall, hope this works.
Thanks for the advice.

---

### Post by colinsr1187 on 2008-08-17
Thanks for the help CalJohn, and AJGreeny, I successfully installed Ubuntu.  Someone should post an update on the Msi Wind triple boot installation Wiki page.  Might prevent the next person from going thru the hassle I did.

---

### Post by colinsr1187 on 2008-08-18
Sorry for the newbiness.  I have set up the partitions where XP and OSX are primary, and Ubuntu/Swap and "shared storage" are logical...one problem.  When I log in to XP I cannot see the storage partition.  I can see the OSX.  But not Ubuntu/Swap or Storage.  
Again, I apologize if this is a kindergarten question.

---

### Post by caljohnsmith on 2008-08-18
> **colinsr1187 said:**
> Sorry for the newbiness.  I have set up the partitions where XP and OSX are primary, and Ubuntu/Swap and "shared storage" are logical...one problem.  When I log in to XP I cannot see the storage partition.  I can see the OSX.  But not Ubuntu/Swap or Storage.  
Again, I apologize if this is a kindergarten question.
What file system is the storage partition? Also to view Ubuntu's partition in Windows, you can use this great free program called [ext2fsd]("http://sourceforge.net/projects/ext2fsd/?abmode=1"). That program allows you to access ext2 or ext3 partitions (like Ubuntu) in Windows.

---

### Post by colinsr1187 on 2008-08-18
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b926d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5227    41985846    7  HPFS/NTFS
/dev/sda2            5228       10454    41985877+  af  Unknown
/dev/sda3           10455       38913   228596917+   5  Extended
/dev/sda5           10455       15681    41985846   83  Linux
/dev/sda6           15682       16191     4096543+  82  Linux swap / Solaris
/dev/sda7           16192       38913   182514433+   7  HPFS/NTFS
msiwind@msiwind-laptop:~$ 


Is this setup correctly?
XP, OSX, Ubuntu/Swap, Shared

---

### Post by caljohnsmith on 2008-08-18
OK, if sda7 is your shared partition, then it has an NTFS file system according to fdisk. That should show up in Windows without any additional software, but if you are having troubles getting Windows to see that partition, maybe it is because it is on a logical partition instead of primary. All my logical partitions on my HDD are not NTFS, so I don't know offhand if there are any issues with logical NTFS partitions being recognized by Windows.

---

