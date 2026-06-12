---
title: "Ubuntu installer and gparted can't see partition table"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by faiuwle on 2013-04-08
I have a brand new Asus laptop with Windows 7 preinstalled on it, and I'm trying to get it to dual-boot Ubuntu 12.04, but I haven't done any partitioning of this disk yet because neither the Ubuntu installer nor gparted can detect the existing Windows partition.  Running from the liveCD, I get the exact same error messages that this person had here: [http://ubuntuforums.org/showthread.php?t=1744799](http://ubuntuforums.org/showthread.php?t=1744799).

Instead of coming with a Windows recovery DVD, the computer came with a "recovery partition" which is accessible by typing F9 during boot.  This is a 750 GB disk, but the disk management utility in Windows (which thinks everything is fine and has an MBR partition scheme) shows the Windows partition as only ~700 GB, and gparted shows the same amount of "unpartitioned" space.  This makes me think that the recovery partition is somehow hiding itself on the computer and messing with the partition information.  The people at Asus will not answer any questions about partitioning for fear that I will mess something up and it will be their fault.

Will running fixparts fix my disk as it did for the other person, or do I need to do something different?

---

### Post by Bashing-om on 2013-04-08
faiuwle; Hi !

Standard advise is to use the Window's disk utilities to (re)partition the hard disk. And as well UEFI may be a factor (later Windows7 had that boot sector as well as Windows8);
Mark Phelps and oldfred of this forum have excellent advise on dual booting with windows. For starters see:
[http://ubuntuforums.org/showthread.php?t=2126166&page=2](http://ubuntuforums.org/showthread.php?t=2126166&page=2)
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[http://ubuntuforums.org/showthread.php?t=2059640](http://ubuntuforums.org/showthread.php?t=2059640)

Many advise to copy the "recovery" partition to CD disk in order to have a partition available to install ubuntu onto; if the older MBR scheme is used.[INDENT=2]hope this is of some help

[/INDENT]

---

### Post by faiuwle on 2013-04-08
Thanks for the info, but I can't do anything with the recovery partition when it is still invisible to all partitioning utilities.  I have made a clone of my disk with dd, so I can always restore from that.  I also doubt that doing anything with the Windows disk management utility is going to make Ubuntu recognize the partition table, since Windows doesn't think there is anything wrong, and thinks that it has a MBR.

---

### Post by Bashing-om on 2013-04-08
faiuwle;

May I offer that perhaps the hard disk is dynamically( advanced Windows thing) partitioned, In this format linux does not do.
From the liveCD:Terminal code:
```
sudo fdisk -lu
sudo parted -l 
sudo parted /dev/sda unit s print
``` And this perhaps will give some indications of what is going on.[INDENT=3]
worth investigating 
[/INDENT]

---

### Post by faiuwle on 2013-04-08
Well, the disk management utility in Windows gives an option to switch to a dynamic disk, which seems to indicate that it isn't.

sudo fdisk -lu:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdb590021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1465145343   732469248    7  HPFS/NTFS/exFAT
```

sudo parted -l:
```
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? No                                                                

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

The third command just produces the same error message as above, and then quits when I say No.

---

### Post by Bashing-om on 2013-04-08
faiuwle;

Sure looks a good possibility that the disk is formatted dynamically. I am looking now for ways to confirm this from an ubuntu perspective.

Be advised if that disk is dynamic in nature, will have to be converted to "basic" for both operating systems to co-exist on one hard disk.

I do not do Windows, so I must look at this from my ubuntu experience, with the tools I can locate in ubuntu.
[INDENT=3]
I'll be back

[/INDENT]

---

### Post by Bashing-om on 2013-04-08
faiuwle;

I am back, and some what confused now:
> 
If you wish to find out if your disk is a Basic or a Dynamic one from  the Ubuntu Live CD, run following command in Terminal (Applications >  Accessories).

sudo fdisk -l

If the output contains "SFS", probably you've got Dynamic disk. Time to go back to Windows and convert the disks.
As your "fdisk" output does not indicate dynamic partitioning, back to the drawing board.

There has to be another reason the partitioning is not detected, -> look'n ![INDENT=3]
I'll be back

[/INDENT]

---

### Post by Bashing-om on 2013-04-08
faiuwle;

See if this thread and oldfred's advise is not pertinent to your install:
[http://ubuntuforums.org/showthread.php?t=2132913&highlight=GPT+windows](http://ubuntuforums.org/showthread.php?t=2132913&highlight=GPT+windows)[INDENT=2]
I desire that you be up on ubuntu

[/INDENT]

---

### Post by faiuwle on 2013-04-08
That doesn't seem relevant, since my disk is not a GPT disk and uses a MBR.

---

### Post by darkod on 2013-04-09
> **faiuwle said:**
> That doesn't seem relevant, since my disk is not a GPT disk and uses a MBR.

Not exactly. At some point in the past the disk did have gpt table and windows was used to create new msdos table (or mbr table if you want to call it that).

But the wonderful product of Microsoft doesn't do the job properly, as usual. It doesn't delete the backup gpt table when creating the msdos, so linux tools get confused. That's what parted is trying to tell you, you have gpt traces.

Open the disk with fixparts from live mode and it will sort it out for you. There is a .deb to install in live mode and after that simply open the disk with it in terminal, it will offer to sort the problem.
[www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

---

