---
title: "Messed up drive during Marverik installation, HELP"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by biltong on 2010-11-26
Hi everyone, 

I just did a new upgrade to Maverik, however I accidentally messed up my second hard drive in the process.  I have read up on data recovery stuff and there are tons of tool... but I need to know what happened, then I can worry about the fixing.

Ok, Standard P4 PC with two HDDs.
1 X 120GB for / & /Home
1 X 350GB for /Data

During the install I told the setup my second HDD is /Home (who knows why?? -stupid I know) and that its EXT4. (no format)

Now I have a lovely clean HDD with /home. :-P

What happened here now??... There were no partition changes made, I did not format the drive.  AND most importantly... how do I fix it????

PLEASE ANYONE?!?!

---

### Post by lmarmisa on 2010-11-27
Boot your system into a Ubuntu Live CD, open a terminal, type this command and post its output:

```

sudo fdisk -l

```

---

### Post by wet-willy on 2010-11-27
What format did the drive have originally...and what is it now? /etc/fstab will tell.
If all the data is gone as you mention it's a nice clean drive, means it got formatted. If so, your only avenue for data recovery is with a data carver.

---

### Post by Rubi1200 on 2010-11-27
As long as you have not attempted to write anything to the drive, there is a chance for data recovery using Testdisk.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by biltong on 2010-11-28
Hi all,

Here are the details of the two disks in use.  sdb is the problem child.
I upgraded from Koala... which I think still had EXT3.. so in this case I guess the file system changed to EXT4.

**To lmarmisa: (output from fdisk -l)**

fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b746

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14374   115453952   83  Linux
/dev/sda2           14374       14947     4603905    5  Extended
/dev/sda5           14374       14947     4603904   82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bb7eb84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    f  W95 Ext'd (LBA)
/dev/sdb5               1       29797   239344339+  83  Linux
/dev/sdb6           29798       36483    53705263+   c  W95 FAT32 (LBA)


**To wet-willy: (output /etc/fstab)**

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a9a3c9ed-9e82-4954-9ad0-354c5ed1504b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c5192983-1b40-45f2-a3f6-69409bc9f23b none            swap    sw              0       0


Thanks for the responses.

---

### Post by wet-willy on 2010-11-28
I find it odd that /dev/sdb is not mounted according to /etc/fstab. Home must be part of / on /dev/sda. And there is a smaller Fat partition at the end of the drive, have you tried mounting it to see what's in there? It should be visible to Windows also.

---

### Post by biltong on 2010-11-28
> **wet-willy said:**
> I find it odd that /dev/sdb is not mounted according to /etc/fstab. Home must be part of / on /dev/sda. And there is a smaller Fat partition at the end of the drive, have you tried mounting it to see what's in there? It should be visible to Windows also.

Actually once I realised my mistake, I re-installed the PC using the option "Entire disk" on sda....without mounts to sdb.  So now the fstab does not have any info on sdb.

---

### Post by lmarmisa on 2010-11-28
> **biltong said:**
> Actually once I realised my mistake, I re-installed the PC using the option "Entire disk" on sda....without mounts to sdb.  So now the fstab does not have any info on sdb.

You wish to fix the partition. But, what is your purpose?. Do you want to try to recover the lost files?. This could be very difficult. Or simply do you wish to create a NTFS partition in /dev/sdb5?. This is not difficult.

---

### Post by biltong on 2010-11-28
> **lmarmisa said:**
> You wish to fix the partition. But, what is your purpose?. Do you want to try to recover the lost files?. This could be very difficult. Or simply do you wish to create a NTFS partition in /dev/sdb5?. This is not difficult.

As mentioned before, I did not create any new partitions nor did I format the drive on sdb.  However I think that I changed the file system from EXT3 to EXT4 which caused the data to disappear.

How I have to figure out how to get my data back.  Will changing the file system from EXT4 to EXT3 "restore" my data? or do I need to start digging deeper with tools like photorec or data carver?

---

### Post by oldfred on 2010-11-29
Was all you data in one partition. Testdisk my recover partitions, if not then you have to use photorec to recover files.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by biltong on 2010-11-29
> **oldfred said:**
> Was all you data in one partition. Testdisk my recover partitions, if not then you have to use photorec to recover files.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

Oh boy, looks like I've hot no other option but to do data recovery :-(

---

