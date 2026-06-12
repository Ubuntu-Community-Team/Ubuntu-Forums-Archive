---
title: "Unable to increase disk vol (will forcibly become &quot;dynamic&quot; which means I can't boot)"
date: 2016-11-25
forum: Installation &amp; Upgrades
---

### Post by Jerriy on 2016-11-25
I have a dual boot laptop w/ Windows on one disk (in windows parlance "disk 0" or "C drive") and Ubuntu 16.04 installed on the second disk aka "1" aka "D". I have enough unallocated space on so I wanted to expand the windows backup partition which is not on C drive but D, together with Ubuntu. But if I try to expand that I get warning that the whole disk will become "dynamic" which will be a bad thing: I will no longer be able to start any of the installed OS because apparently the Grub dual boot menu thing is also installed on that second disk and will be destroyed by that disk becoming "dynamic". Which means I will not only lose the access to Ubuntu (on that disk) but I will also NOT be able to start Windows even though it is on another disk (since I get to Windows from the grub dual boot menu).

So the question is how do I proceed to expand my partition without touching Windows? Do I have to reinstall Ubuntu in some different way than it is now (default)? 

If so how? 

Ideally there is a way to "save" the grub dual boot menu to "C" drive, and therefore access Windows alone (for the time being) even if Ubuntu OS no longer works due to the disk becoming dynamic and me proceeding to tinker with the partitions there.

---

### Post by oldfred on 2016-11-25
Do you really have two physical drives, or just two partitions?
Windows confuses the issue. In Linux you have drives like sda, sdb and partitions like sda1, sda2, sdb1, etc.

Post this from terminal in live installer:
sudo parted -l

Do not let Windows convert to dyanmic, that is proprietary to Microsoft. Newest Ubuntu seems to now recognize it, where before it just did not work at all.
You want to create an extended partition which then can have as many logical partitions as you want.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Jerriy on 2016-11-25
> **oldfred said:**
> Do you really have two physical drives, or just two partitions?
Windows confuses the issue. In Linux you have drives like sda, sdb and partitions like sda1, sda2, sdb1, etc.

Post this from terminal in live installer:
sudo parted -l- 1 HDD,
- 2 drives/disks
- multiple partitions on each

```
Model: ATA WDC WD5000BPVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  19,3GB  19,3GB  primary  ntfs         diag
 2      19,3GB  19,4GB  88,1MB  primary  ntfs         boot
 3      19,4GB  500GB   481GB   primary  ntfs


Model: ATA WDC WD5000BPVT-2 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  26,2GB  26,2GB  primary   ntfs
 2      26,2GB  136GB   110GB   extended
 5      26,2GB  126GB   100GB   logical   ext4
 6      126GB   136GB   9999MB  logical   linux-swap(v1)


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 9999MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0,00B  9999MB  9999MB  linux-swap(v1)


```

---

### Post by Jerriy on 2016-11-25
Hmm... your terminal command seems to have revealed a third one - must be one of those "Q" drive type invisible things

---

### Post by oldfred on 2016-11-25
If you do an encrypted install it may show that differently.
Loop mount is an internal mount, not a real device.

If you are trying to enlarge the NTFS partition on sdb, you have to do several things.
First shink the ext4 partition and then move it right on drive. Make sure you have good backups as any major partition changes can corrupt drive, particularly if interrupted in the middle. And a move can take a long time. Then you have to move the extended partition to in effect move the unallocated from inside the extended to outside the extended. Then you have room to expand the NTFS into the unallocated.

But it does not look like you have full used all the space on sdb. You could expand the extended partition to take up the rest of the drive and make a large NTFS partition as logical. 

I typically make / (root) only 25GB but have all my data in another partition. I do not have Windows anymore but back with XP I had a shared NTFS data partition. Then added a shared ext4 partition and as I retired Windows more & more data went into the ext4 partition.

---

### Post by Jerriy on 2016-11-25
Are you suggesting it's easier to create a whole new NTFS partition (on the unallocated) and then be done with it? (so that I don't have to move the ubuntu stuff (ext4)?

That's fine by me.
 
At least if there is a way to delete the existing NTFS partition. But even if that's not possible, right now my priority is the creation of this bigger NTFS. My plan is to later on optimize in greater detail and reduce the Ubuntu partition.

---

### Post by oldfred on 2016-11-25
It looks like you have about half the drive unallocated. So if that is enough room then that would be easier. But best to make sure it is a logical partition, which means you have to expand extended partition first.

---

### Post by Jerriy on 2016-11-26
How do I do these things exactly - both the expansion and the making of a new "logical" NTFS (I'm not on ubuntu exclusively so sorry for not being up to date)

---

### Post by yancek on 2016-11-26
If you are using GParted from Ubuntu, you would first need to unmount the partitions you want to modify.  The link below is a basic tutorial and the second link is the actual GParted Manual.

[https://ubuntu-mate.community/t/gparted-partition-guide-for-linux-and-windows-users/797](https://ubuntu-mate.community/t/gparted-partition-guide-for-linux-and-windows-users/797)

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

