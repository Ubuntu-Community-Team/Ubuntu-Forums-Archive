---
title: "Help with setting up a MDADM Linear RAID"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by radiocognition on 2008-01-06
Hey All,

Ive been using Ubuntu for about five months now and I am currently setting up a system to act as a simple Samba file server for a windows network.  I have no problems setting up the sharing . . . I had just wanted to setup a simple linear software RAID to be able to mount two hard drives as one folder (that would later be shared).  One of the hardives is a 120 GB SCSI, while the other is a 80 GB SATA.

After doing some reading, I decided to set up the RAID using MDADM.  After installing MDADM I ran the following command:

```
sudo mdadm --create --verbose /dev/md0 --level=linear --raid-devices=2 /dev/hdc1 /dev/sca1
```

This created my RAID Array.  After using the --scan command to find the UUID of the array, I modified the /ect/mdadm/mdadm.conf file to include the devices and the new array.

```

DEVICE /dev/hdc1 /dev/sda1
ARRAY /dev/md0 level=linear num-devices=2 UUID=9a3be8d5:e657f0fe:4125399c:71910b5c
```

The array exists and is running.  Running a --detail query gives the following output:

```
Version : 00.90.03
  Creation Time : Sat Jan  5 21:52:29 2008
     Raid Level : linear
     Array Size : 197631424 (188.48 GiB 202.37 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jan  5 21:52:29 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

       Rounding : 64K

           UUID : 9a3be8d5:e657f0fe:4125399c:71910b5c (local to host true-desktop)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0      22        1        0      active sync   /dev/hdc1
       1       8        1        1      active sync   /dev/sda1
```

Now here is where I am stuck.  I cannont mount my array as I could to a normal hard drive.  Gparted can see the array device, but gives the following warning:

[I]```
e2label: No such file or directory while trying to open /dev/md0p1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: No such file or directory while trying to open /dev/md0p1

Unable to read the contents of this filesystem!
Because of this some operations may be unavaliable.
```[/I]

What is going on? If the raid has been created how can I not mount it?  The --detail command output states that the superblock is persistant, but Gparted still cant find a valid filesystem superblock.  I feel like I am 90% the way there and am missing just the last step.

---

### Post by samosamo on 2008-01-06
You can't mount it because it has no filesystem yet.  You have to create a filesystem on the raid device. Are you reading a tutorial?  Find the step with "mkfs" command.

---

### Post by radiocognition on 2008-01-06
ive been gleaning information from a handful of pages here and there, but havent fount anything about setting up a file system.  Can you refer me to something that would be able to point me in the right direction?  Any help would be appreciated.

---

### Post by radiocognition on 2008-01-06
Just got it working.  I used the mkfs command to reformat the array
```
mkfs -j /dev/md0
```

Once the reformat finished I was able to mount the drive to a folder "Share"

```
mount /dev/md0 /media/Share
```

---

