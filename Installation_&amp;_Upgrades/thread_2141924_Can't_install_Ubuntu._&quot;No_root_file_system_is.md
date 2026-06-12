---
title: "Can't install Ubuntu. &quot;No root file system is defined” error"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by postt on 2013-05-04
I made an USB installer using Pendrive Linux. I runs Ubuntu off that USB drive. Everything works fine.


  Then I tried to actually install Ubuntu on my local drive and it won't  let me. I have a mSATA SSD drive. It's a new raw drive. It's the only  drive in the computer.


  I used GParted to make a /dev/sda1 ext4 partition there. But the installer is not seeing it. It gives me a screen that looks like this:

  [URL="http://oi53.tinypic.com/25u14q9.jpg"]http://oi53.tinypic.com/25u14q9.jpg

[/URL]
On that installer screen all options are greyed out. No actions can be performed. I guess that partition never becomes part of the file system and I need to make it into a root filesystem? How do I do that?


  I tried Ubuntu, Xubuntu, and Mint and all 3 installers crashed at that very step. 

This is much harder than I expected. Can any experts help me? I've spent hours on this going nowhere and really don't know what to do.

---

### Post by darkod on 2013-05-04
Boot into live mode, open terminal and try something like this:
```
sudo dmraid -Er /dev/sda
```

This usually happens if there is raid meta data on the disk. That command will remove the meta data.

Or maybe there is some partitioning error, in that case it wouldn't show any partitions. Also post the output of this in terminal:
```
sudo parted -l
```

---

### Post by postt on 2013-05-04
> **darkod said:**
> Boot into live mode, open terminal and try something like this:
```
sudo dmraid -Er /dev/sda
```

This usually happens if there is raid meta data on the disk. That command will remove the meta data.

Or maybe there is some partitioning error, in that case it wouldn't show any partitions. Also post the output of this in terminal:
```
sudo parted -l
```

Thanks for the response.

I actually saw a similar problem on another forum and the guy said 

```
sudo apt-get remove dmraid
```

would solve the problem. I tried it and it did! Ubuntu is now installing.

I still don't understand how removing RAID software has anything to do with installing Ubuntu. Can you explain? 

This is way harder than I expected.

---

### Post by darkod on 2013-05-04
That is a temporary solution. I assume the disk still has meta data, only removing the dmraid package made the installer not see it. When you reinstall in the future you will have the same problem since the meta data is still there.

The disk was probably set up as raid earlier, or as a caching SSD which is a type of raid (that's how they set it up). If the installer detects a disk with raid meta data, it ignores it thinking it's part of a raid array, since you install onto raid in different way. Otherwise if the installer forces to install on a disk member of raid, it will break the array. That's why it ignores disks with meta data. But many disks these days have meta data since people use them and don't clean them up later. Also manufacturers have started using meta data for the caching SSDs they install to speed up windows, etc.

My command would have removed the meta data, and you don't need to remove the package dmraid.

---

### Post by postt on 2013-05-04
The disk is a mSATA SSD. That must be why it has raid meta data.
 
Output of ```
sudo parted -l
``` is

```
Model: ATA OCZ-NOCTI (scsi)Disk /dev/sda: 30.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  7904MB  7903MB  primary   ext4            boot
 2      7905MB  30.0GB  22.1GB  extended
 5      7905MB  8888MB  983MB   logical   linux-swap(v1)
 6      8889MB  30.0GB  21.1GB  logical   ext4

```

I have installed Ubuntu and am now running Ubuntu off the local drive. Is it still safe to run your command now?

---

### Post by darkod on 2013-05-04
It should be. That command only removes any meta data remains and does not touch the data. The system should keep working as normal.

---

### Post by postt on 2013-05-04
I reinstalled dmraid and run

```
sudo dmraid -Er /dev/sda
```

And got this:

```
no raid disks and with names: "/dev/sda"
```

What to do now?

---

### Post by darkod on 2013-05-05
Then it looks like it's clean from meta data. But in that case it's strange how it didn't want to use the disk until you removed dmraid. If the disk didn't have meta data, removing dmraid shouldn't matter.

You can keep using it as it is, no problem. I would double check the bios settings, whether the SATA mode is set to AHCI and not RAID, or similar.

---

