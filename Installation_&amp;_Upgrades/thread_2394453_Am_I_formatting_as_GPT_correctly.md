---
title: "Am I formatting as GPT correctly?"
date: 2018-06-16
forum: Installation &amp; Upgrades
---

### Post by A Traveller on 2018-06-16
Hi all.

As posted in another thread, I have had all kinds of problems trying to install Ubuntu and have now given up for the moment. I decided to install an OS not based on Ubuntu/Debian and the installation process didn't go so smoothly with that either, until I formatted my hard drive in my usual old method, i.e. format the drive as Master Boot Record, have one main ext partition and small swap space partition. It worked fine then.

I was wondering if anyone could confirm if my method of formatting as GPT is correct or if I am doing something wrong that could be causing problems in installing Ubuntu or another Linux OS, please.

Please forgive me if I cannot remember the exact terminology of items as I am going to try explaining partly from memory.

The following is what I have been doing to install as GPT, but not have been successful on any occasion.

In Ubuntu's Disk Utility, highlight each partition and press 'Delete Partition'.
Click 'Format Drive'.
Choose 'GUID Partition Table' and click 'Format'.
Cannot remember the exact steps, but:
Create a small 1Mb (0.001 Gb) partition at the beginning as 'Empty Space' and choose the option that makes 'BIOS_flag' appear next to it when viewed in Gparted (can't remember what it's called). Please note that in GParted, a triangle with an exclamation mark in it always appears next to this partition with the remark 'unknown'.
Create the main ext 4 partition.
Create a 'swap space' partition at the end.

Now during installation of ubuntu, I usually receive an error about formatting, at which point, I double-click on the main ext4 partition, e.g. /dev/sda1, choose ext4 from the list (I think it says something like ext4 journalling system) and choose just '/' from the dropdown list for the mount point. Ubuntu accepts these changes and does not then give me the error. When it's time to install, I highlight the partition without the number on the end, e.g. /dev/sda, not /dev/sda1, etc.

For device for bootloader installation, I choose, e.g. /dev/sda (without any number on the end).

At some point, somewhere, there is a checkbox which says 'Required/Firmware'. I leave this unchecked.
I always leave 'Take ownership of filesystem' checked'.

I then carry on with the installation.

Again, I am sorry that I can't remember the exact terms of things but I am counting on you knowledgeable folk to know exactly what I am referring to in each step.

Thanks for any help.

---

### Post by TheFu on 2018-06-16
I've never used "Disks".
I always use either gparted, parted, or fdisk, in that order of preference.  gparted doesn't work on servers, so dropping back to CLI versions is necessary.  These tools also work for partition creation.  For creating a file system (or not), I think only gparted can do that, but you can use mkfs (or is it newfs?) directly to do that.  On file systems smaller than 10G, it is handy to create 10-100x more inodes than will be made by default with any tool,  but especially GUI tools.  Plus for pure data partitions, it is nice to remove all the reserved space (for root use only).  That can be done later using tune2fs.  Don't remove the reserved space for OS or application partitions, however.  But those should never be over 20-25G in size anyways.

Whether you need extra partitions or not is dependent on whether you are booting with BIOS (legcay) or UEFI.  On Linux, the partition table type doesn't matter at all.

---

### Post by Dennis N on 2018-06-16
Isn't Ubuntu going to be the only OS to be on the disk? Why don't you use the option in the installer to use the entire disk? It should handle the partition table, all the partition work, and installation automatically. Might default to MBR, but that is ok for a BIOS computer.

---

### Post by oldfred on 2018-06-16
I use gparted or gdisk, never used Disks as early versions seemed to have issues with gpt.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[*]/swapfile                                 none            swap    sw              0       0
[/LIST]

Gparted will also show an error on bios_grub as it is unformatted. It also shows errors on Windows System reserved as it is also unformatted. But both have valid GUIDs so gparted should be smart enough to know they are correct.

---

### Post by A Traveller on 2018-06-18
Thanks for all the replies.

TheFu, I am booting with BIOS.

Dennis N, yes, there would only be one OS on the disk. I have been formatting disks for Ubuntu/installing Ubuntu since 6.06 and have always used Fdisk or Disk Utility. All of them have been as MBR. More recently, I started to use GParted, which I did use when trying to install my Ubuntu recently, however, it is GPT that I wanted to format the disk as so I know how to do it and that it works if needed in future, not because I 'needed' to on this occasion and I'm pretty sure that I've done it right, but just wanted it confirmed in case there was something that I wasn't understanding that may have been contributing to my unsuccessful Ubuntu installations.

Thanks oldfred.

---

### Post by TheFu on 2018-06-18
If you will continue to boot with BIOS, then you can treat GPT partitions just like MBR partitions.
I have a BIOS booting system with GPT partition table. I use LVM, so the layout isn't as clear.
```
$ sudo fdisk -l /dev/sdb
Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DB92F312-7D21-4BF3-8F14-C6CE5E29E72D

Device      Start        End    Sectors  Size Type
/dev/sdb1    2048       4095       2048    1M BIOS boot
/dev/sdb2    4096     503807     499712  244M Microsoft basic data
/dev/sdb3  503808 7814035455 7813531648  3.7T Linux LVM
```

The LVM layout from lsblk is:
```
sdb                                   8:16   0   3.7T  0 disk 
&#9500;&#9472;sdb1                                8:17   0     1M  0 part 
&#9500;&#9472;sdb2                                8:18   0   244M  0 part /boot
&#9492;&#9472;sdb3                                8:19   0   3.7T  0 part 
  &#9500;&#9472;istar--vg-root                  252:0    0 102.3G  0 lvm  /
  &#9500;&#9472;istar--vg-swap_1                252:3    0   3.6G  0 lvm  [SWAP]
  &#9492;&#9472;istar--vg-lv_media              252:4    0   3.5T  0 lvm  /D
```

sdb1 is a 1M placeholder that I created to ensure partition alignment.  I think only 4K is needed, but ...  what is 1MB on a 4TB disk?  It is not used in any way. It doesn't have any file system or any data.

and just for clarity (I've removed unimportant storage and fake partitions):
```
$ df -Th
Filesystem                                   Type      Size  Used Avail Use% Mounted on
/dev/sdb2                                    ext2      237M  102M  123M  46% /boot
/dev/mapper/istar--vg-root                   ext4      101G   57G   40G  60% /
/dev/mapper/istar--vg-lv_media               ext4      3.5T  3.4T  115G  97% /D

```

Why is it sdb and not sda?  Because the system has had 2 disk failures over the years and I've moved SATA  cables around to help determine which of the 8 disks connected had failed.  I know now to label each disk with the WWN where it can be seen without having to pull the disks from any array or slots first.

There are lots and lots of other disks connected to this machine. It is a plex media server.  / is 100G because plex stores all sorts of crap deep in the "/var/lib/plexmediaserver/Library/Application Support/Plex Media Server" directories.  Yes, the first used plex directory is THAT FREAKIN' deep - about 50 characters too long for absolutely zero reason I can understand.  I've considered making a new LV just for plex data to keep the OS LV less than 25G, which is a best practice.

Anyway, hope this is a concrete, helpful, example.

---

### Post by A Traveller on 2018-06-20
Thanks for taking the time to provide such a thorough response, Fu. It has been appreciated.

---

