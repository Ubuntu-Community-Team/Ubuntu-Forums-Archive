---
title: "Partitions not recognized in Ubuntu"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by hafeez-ur-rehman on 2008-07-20
hi, I have installed ubuntu8.04. And I am unable to see/access 5 out of 6 existing partitions which i had before installation.
My issue is quite similar to the people in the thread mentioned below but with the difference that I have installed and now I want to access the drives/partitions.
```
http://ubuntuforums.org/showthread.php?t=808757&highlight=partitions+ubuntu!
```

```
sudo fdisk -l
```

```
/dev/sda1            2370        2431      498015   82  Linux swap / Solaris
/dev/sda2   *           1        2369    19028961   83  Linux
/dev/sda3            2432       19458   136755032   42  SFS

Partition table entries are not in disk order
```

the above is after installation. I have 160GB HDD and I believe that the rest of the 5 partitions(130GB) are intact and just inaccessible.
please help.

---

### Post by louieb on 2008-07-20
Did some Google on **partition type 42 SFS**. Seems it could be some kind of NTFS partition for windows 2000.   
Might try to access it as an NTFS partition.
```
sudo mkdir /media/windows 
sudo mount /dev/sda3 /media/windows/ -t ntfs -o nls=utf8,umask=0222 
```
and use the file browser to navigate to /media/windows to see whats there.

---

### Post by hafeez-ur-rehman on 2008-07-20
Yes u are right i had NTFS partitions in Vista.
one more thing i repartitioned drives with vista's builtin software some weeks back and repartitioned using "Partition Editor" with live CD to get 3 small chunks of about 1MB,4MB and 8MB.
I thought this information might help.


```
sudo mount /dev/sda3 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

```
NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

---

### Post by louieb on 2008-07-21
Don't think I'm going to be of any help getting Linux to read your type 42 SFS partition. Haven't been able to find anything short of compiling a kernel with experimental SFS support. Even that thread did not say if it worked or not.  Good luck. 
> 
**42  Linux swap (sharing disk with DRDOS)** 
 

**42  SFS (Secure Filesystem)**SFS is an encrypted filesystem driver for DOS on 386+ PCs, written by Peter Gutmann. 
 
**42  Windows 2000 marker**If a partition table entry of type 0x42 is present in the legacy partition table, then W2K ignores the legacy partition table and uses a proprietary partition table and a proprietary partitioning scheme (LDM or DDM). As the Microsoft KnowledgeBase writes: *Pure dynamic disks (those not containing any hard-linked partitions) have only a single partition table entry (type **42**) to define the entire disk. Dynamic disks store their volume configuration in a database located in a 1-MB private region at the end of each dynamic disk.* 

from [http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

---

### Post by fowie on 2008-07-21
Are your partitions Windows Vista software RAID?  A software RAID set up through windows will show up as SFS also.  Don't expect to be able to access that via Ubuntu.

---

### Post by hafeez-ur-rehman on 2008-07-22
Thanx for your help. It was informative as well. I'll read a bit more about it.
My problem has been solved. I repartitioned and recovered with loss of 5% data.

---

