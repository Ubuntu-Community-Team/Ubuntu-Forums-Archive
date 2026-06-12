---
title: "[SOLVED] Unable to create XFS partition"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by nattugglan on 2007-05-10
Hi!

I want to create an XFS partition to use for MythTV recordings.
I've stumbled upon a couple of problems though..

When I try to create an XFS partition during the initial Ubuntu 7.04 feisty install, the size of the XFS partition I want to create isn't accepted.

The hard drive is a 500 GB SATA, and the settings for the partitions I want on the disk are the following.

1
```
Primary
20 000
Beginning
ext3
/
```

2
```
Primary
5 000
Beginning
Swap
```

3
```
Primary
475 100 (max free space)
Beginning
XFS
/home (or /var/lib)
```

The problem is that the max free space (475 100 MB) is not what I get. The XFS partition only becomes 45 600 MB, and 429 499 MB free space is left at the end!
I've tried rebooting and starting over a number of times, but the same happens each time.

When this didn't work I just went ahead and installed feisty on the entire drive instead - and connected another 500 GB SATA drive to use for the recordings.
But when I try to format the second drive using GParted, XFS is greyed out and cannot be chosen.

Does anyone know why XFS is greyed out in GParted? 
Or why XFS on the remaining free space fails during the install?

The weird thing is that choosing XFS for the remaining free space during the install worked on a 100 GB SATA, but doesn't work on the 500..

nattugglan

---

### Post by nattugglan on 2007-05-10
Ok, now this is weird..
When I try to create a single 20 GB ext3 partition on the second 500 GB SATA drive I get the following error message in GParted:

```
**An error occurred while applying the operations**
The following operation could not be applied to disk:

Create Primary Partition #1 (ext3, 20.00 GiB) on /dev/sdb

See the details for more information
```

In the background the new partition gets mounted as *"disk"* (/media/disk) showing a *lost+found* folder, and the details on the error message is:
```
**mkfs.ext3 /dev/sdb1**
mke2fs 1.40-WIP (14-Nov-2006)
/dev/sdb1 is mounted; will not make a filesystem here!
```

Why on earth does this pop up? ](*,) 

nattugglan

---

### Post by nattugglan on 2007-05-10
Update.
GParted LiveCD works. No problems at all.

nattugglan

---

### Post by WilDCarD418 on 2008-01-02
More helpful info (hopefully).
I noticed the live cd version of gparted would format xfs, but the version I have installed (1.7.1) wouldn't. 

```
sudo apt-get install xfsprogs
```


Now it works.

---

