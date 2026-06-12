---
title: "Root getting &quot;permission denied&quot; on some system files"
date: 2018-01-20
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-01-20
I recently upgraded on of my machines. Something when wrong during that upgrade and I've having a lot of trouble straightening it out.

The latest problem I've uncovered is that two file are completely inaccessible. the files are

/var/lib/dpkg/arch
/var/lib/dpkg/triggers

Looking at another machine arch seem to be text file with architecture and is very small triggers is a directory which contains a number of files.

When doing a long list of these files there is no information including modes, date and size. Attempting change to the files as root gets "permission denied" whether I chmod chown or rm.  Using start  to get the inode also results in "permission denied".

The more I investigate them more files I find with this problem. Is there anyway to clear this up?

---

### Post by DuckHook on 2018-01-20
Failing disk? When such stuff happens, my first instinct is to back up all my data so that the problem will be, at most, an inconvenience.

Then run fsck. A corrupted file system can give the symptoms you've described. You may have to run fsck using a LiveUSB.

---

### Post by DuckHook on 2018-01-20
A further note. Failed upgrades are notoriously hard to solve. I don't want to hold out false hopes. Make sure you are in a position to reinstall from scratch without too much trouble.

---

### Post by rsteinmetz70112 on 2018-01-20
> **DuckHook said:**
> A further note. Failed upgrades are notoriously hard to solve. I don't want to hold out false hopes. Make sure you are in a position to reinstall from scratch without too much trouble.

I can reinstall but it will be a lot of trouble.

I can boot into an older kernel and that runs fine. That's what leads me to believe it's the upgrade.

I'm trying to figure out exactly what the problem is. I don't think the hard drive is bad, all of the SMART tests are OK. I may have file system trouble. I may have some other hardware problem.

I can boot into an older kernel and that runs fine. That's what leads me to believe it's the upgrade.

All of my data is backed and redundant, I confident I won''t lose anything important.

---

### Post by DuckHook on 2018-01-20
> **rsteinmetz70112 said:**
> …I can boot into an older kernel and that runs fine. That's what leads me to believe it's the upgrade.
This is useful info. Perhaps you should tell us more detail about your upgrade, your new kernel, your old kernel, etc. Did the upgrade complete or was it truncated? What version were you running before and what version is new?
Please post results of:```
lsb_release -a
``````
uname -a
``````
sudo parted -l print
``````
ls -la /boot
```
> All of my data is backed and redundant, I confident I won''t lose anything important.Excellent. You have the freedom to try a few things.

---

### Post by DuckHook on 2018-01-20
I am stepping out for a few hours. Not back until &#8776; 04:00 UTC,

---

### Post by rsteinmetz70112 on 2018-01-20
> **DuckHook said:**
> This is useful info. Perhaps you should tell us more detail about your upgrade, your new kernel, your old kernel, etc. Did the upgrade complete or was it truncated? What version were you running before and what version is new?
Please post results of:```
lsb_release -a
```
```
~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
```

```
uname -a
```
4.4.0-109 although 103 is the one that boots.
```
# uname -a
Linux romulus 4.4.0-103-generic #126-Ubuntu SMP Mon Dec 4 16:23:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
```
sudo parted -l print
```
```
# parted -l print
Model: ATA ST3320620AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary               raid


Model: ATA ST3320620AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary               raid


Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      65.8MB  8003MB  7937MB  primary  linux-swap(v1)
 2      8003MB  80.0GB  72.0GB  primary                  raid
 3      80.0GB  500GB   420GB   primary                  raid


Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8003MB  8003MB  primary  reiserfs
 2      8003MB  80.0GB  72.0GB  primary               boot, raid
 3      80.0GB  500GB   420GB   primary               raid


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/user-home: 420GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  420GB  420GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-var: 10.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  10.7GB  10.7GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-tmp: 10.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  10.7GB  10.7GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/data-files: 194GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  194GB  194GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/data-home: 126GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  126GB  126GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-usr: 42.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  42.0GB  42.0GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-root: 8590MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  8590MB  8590MB  reiserfs


Error: /dev/md0: unrecognised disk label
Model: Linux Software RAID Array (md)                                     
Disk /dev/md0: 72.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Error: /dev/md1: unrecognised disk label
Model: Linux Software RAID Array (md)                                     
Disk /dev/md1: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/md2: unrecognised disk label
Model: Linux Software RAID Array (md)                                     
Disk /dev/md2: 420GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

root@romulus:~# ^C
root@romulus:~# parted -l print
Model: ATA ST3320620AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary               raid


Model: ATA ST3320620AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary               raid


Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      65.8MB  8003MB  7937MB  primary  linux-swap(v1)
 2      8003MB  80.0GB  72.0GB  primary                  raid
 3      80.0GB  500GB   420GB   primary                  raid


Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8003MB  8003MB  primary  reiserfs
 2      8003MB  80.0GB  72.0GB  primary               boot, raid
 3      80.0GB  500GB   420GB   primary               raid


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/user-home: 420GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  420GB  420GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-var: 10.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  10.7GB  10.7GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-tmp: 10.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  10.7GB  10.7GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/data-files: 194GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  194GB  194GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/data-home: 126GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  126GB  126GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-usr: 42.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  42.0GB  42.0GB  reiserfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/romulus-root: 8590MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  8590MB  8590MB  reiserfs


Error: /dev/md0: unrecognised disk label
Model: Linux Software RAID Array (md)                                     
Disk /dev/md0: 72.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Error: /dev/md1: unrecognised disk label
Model: Linux Software RAID Array (md)                                     
Disk /dev/md1: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/md2: unrecognised disk label
Model: Linux Software RAID Array (md)                                     
Disk /dev/md2: 420GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 
```

```
ls -la /boot
```
```
# ls -la /boot
total 168263
drwxr-xr-x  6 root root     1208 Jan 20 15:41 .
drwxr-xr-x 28 root root      984 Jan 18 16:12 ..
-rw-r--r--  1 root root   646299 Apr  8  2011 abi-2.6.32-31-generic
-rw-r--r--  1 root root  1249214 Dec  4 12:22 abi-4.4.0-103-generic
-rw-r--r--  1 root root  1249214 Dec 11 08:36 abi-4.4.0-104-generic
-rw-r--r--  1 root root  1249330 Jan  9 15:28 abi-4.4.0-109-generic
drwxr-xr-x  3 root root       72 Jun 18  2008 boot
-rw-r--r--  1 root root   110567 Apr  8  2011 config-2.6.32-31-generic
-rw-r--r--  1 root root   190517 Dec  4 12:22 config-4.4.0-103-generic
-rw-r--r--  1 root root   190517 Dec 11 08:36 config-4.4.0-104-generic
-rw-r--r--  1 root root   190533 Jan  9 15:28 config-4.4.0-109-generic
lrwxrwxrwx  1 root root       15 Jun 18  2008 debian.bmp -> /boot/sarge.bmp
drwxr-xr-x  2 root root      472 Jan 18 16:13 grub
-rw-r--r--  1 root root  9427094 Apr 28  2011 initrd.img-2.6.32-31-generic
-rw-r--r--  1 root root 39279043 Jan 20 15:03 initrd.img-4.4.0-103-generic
-rw-r--r--  1 root root 39278030 Jan 20 15:40 initrd.img-4.4.0-104-generic
-rw-r--r--  1 root root 39278580 Jan 20 15:41 initrd.img-4.4.0-109-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root  2158030 Apr  8  2011 System.map-2.6.32-31-generic
-rw-------  1 root root  3887726 Dec  4 12:22 System.map-4.4.0-103-generic
-rw-------  1 root root  3887726 Dec 11 08:36 System.map-4.4.0-104-generic
-rw-------  1 root root  3888874 Jan  9 15:28 System.map-4.4.0-109-generic
-rw-r--r--  1 root root     1336 Apr  8  2011 vmcoreinfo-2.6.32-31-generic
-rw-r--r--  1 root root  4055840 Apr  8  2011 vmlinuz-2.6.32-31-generic
-rw-------  1 root root  7104176 Dec  4 12:22 vmlinuz-4.4.0-103-generic
-rw-------  1 root root  7104112 Dec 11 08:36 vmlinuz-4.4.0-104-generic
-rw-------  1 root root  7104528 Jan  9 15:28 vmlinuz-4.4.0-109-generic
```


Excellent. You have the freedom to try a few things.

I was able to get the system to boot and was able to run the fsck on the /var filesystem. I can now see the files I was having trouble with.
I still am having trouble booting the other kernels. I am also getting a lot of Segmention Faults, which is starting to look like a hardware problem, possibly the motherboard or power supply. The motherboard is fairly new and have been working without problems. It does have a lot of tweaking to adjust memory and cpu speeds.

---

### Post by DuckHook on 2018-01-21
Immediately, I see that I am out of my depth. You are running RAID and reiserfs. I use neither. If I tried to advise you further, I fear that I would only mess things up. I hope that some server guru will see this and dive in.

But here are a few things that will help. Since you know that 4.4.0-103 works, first, let's make sure it sticks around:```
sudo apt install linux-image-4.4.0-103 linux-headers-4.4.0-103 linux-image-extra-4.4.0-103 linux-signed-image-4.4.0-103
```
```
sudo apt-mark hold linux-image-4.4.0-103 linux-headers-3.3.0-103 linux-image-extra-4.4.0-103 linux-signed-image-4.4.0-103
```
Other than that, please wait for someone more knowledgeable on RAID and reiserfs.

If you like, I will move this thread into the Servers subforum where all the server gurus hang out.

---

### Post by rsteinmetz70112 on 2018-01-21
DuckHook

Thank you for your help. As always having someone look at things for you is very helpful. I think I've found the problem. I seem to have had a relatively new Memory Module go bad. This morning I replaced it with new memory and everything seemed to be working at least for now. I'm going to continue to do more testing. I'll start a new thread if I come across other problems.

Apparently the memory failed just before or during my last upgrade and that may have caused a lot of SIGSEGV and other Faults during the upgrade. It certainly was causing a lot of them while I was trying to fix things.

I believe that RAID and reiserfs saved me from data loss although as some point I plan to migrate to ext4 since reiserfs is not being developed as actively as it was.

I'm going to mark this thread as solved.

---

### Post by DuckHook on 2018-01-21
Though my input was little enough, I am very happy that you found the problem and then the solution.

I do not know your specific circumstances but would note the following general things:

[LIST=1]
[*]RAID is essential for always-on servers that cannot afford any downtime. It is problematic for general use. It is complex to administer and in some cases actually makes your system more fragile. However, for all I know, you are a guru and need no lessons from me.
[*]If you are thinking of switching from *reiserfs*, perhaps *ext4* is a backward step. It is a fine filesystem and is so common and central to standard Linux distros that it is well tested and rock solid. But it is now an old technology with limitations. In most cases, I would not think of recommending anything else, but since you already use *reiserfs*, you are used to more capable filesystems. Therefore, in cases like yours, you may wish to consider something like *zfs*. It is now supported in Ubuntu out of the box. It allows snapshots, roll-backs and incremental backups. Even the principal developer of *ext4* himself [recommends more modern filesystems]("https://en.wikipedia.org/wiki/Ext4#Limitations") like *btrfs*, though I am unfamiliar with it.
[/LIST]
My knowledge of *zfs* is quite rudimentary for now. I use it for my LXD containers and have only started exploring its features. But I suspect that a *reiserfs* user would quickly find his/her way around.

---

### Post by rsteinmetz70112 on 2018-01-22
I posted another question asking for input on the file system to use for a reconfiguration of several machines. I suggested ZFS and btrfs which can do raid on their own without mdadm or lvm. That certainly seems attractive. The one response I got was that in a relatively small system like I anticipate (4 1-TB drives in 2 arrays) that ext4 was probably the best. The zfs guides don't seem to recommend it for my use and recommend heavier duty hardware. I still haven't decided. I'm concerned that reiserfs is not really being developed. I'm also a little leary of the multiple layers of software mdadm, lvm2, reiserfs. I am also looking at btrfs which offers in place conversion of existing file systems.

These are servers and have been in use almost continuously since 2006 with several redos of the hardware and upgrades of the OS along the way. At the time I think reiserfs was the only journaling file system supported on Ubuntu, although JFS was possibly available. I don't use the features of the file system features much but the journaling make it more resistant to data loss as does the use of Raid 1 for redundant drives.

---

### Post by DuckHook on 2018-01-22
Just had a chance to go over the thread you referenced. I would not go against TheFu's advice. He knows what he is talking about.

If you are using mdadm and lvm2 anyways, then I would tend to agree with TheFu. ext4 as your base file system will be better than reiserfs. I use zfs firstly to learn about it and secondly to take advantage of its snapshots feature. Other than that, I agree that it is overkill. My memory is no longer reliable going back that far, but I do believe that ext3 would have been available then. Another stable rock-solid file system on which ext4 built a bunch of very useful extensions.

I'm not going to pretend to know more about filesystems than I really do. If you run multiple servers, you may be able to try one of them on ZFS and see how it works.

Good Luck and Happy Ubuntu-ing!

---

