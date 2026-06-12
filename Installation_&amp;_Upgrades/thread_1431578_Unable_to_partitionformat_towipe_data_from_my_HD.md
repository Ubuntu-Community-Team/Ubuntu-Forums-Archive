---
title: "Unable to partition/format to/wipe data from my HD"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by k0brakai on 2010-03-16
Hello all, Recently attempted a Dual boot of XP and Ubuntu. Using a guide that instructed me to create 3 partitions, one for Ubuntu, one for XP and one in the middle to be accessed from both OS' for general data, music files etc. I created these partitions and got on with installing XP. 

I discovered that I couldnt see my "Data" partition from XP and so booted from liveCD to see what was going on. Opened GParted and it showed my whole HD as unallocated, and I cant do anything to this unallocated space. Can't create new partitions, cant format to a new file system. I get an error symbol and a set of keys symbol next to the partition I tried to create. Please see attached screen shot. 

Using the Disk Utility I attempted to delete everything on the disc and create an NTFS file system and got this error: 

Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sda, offset=32256
Entering MS-DOS parser (offset=0, size=120034123776)
MSDOS_MAGIC found
looking at part 0 (offset 98662233600, size 21369277440, type 0x07)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=4
refusing to delete a protected partition


I have also included an fdisk -l readout as I gather (from reading a few posts) that this might be needed to decipher the problem:

ubuntu@ubuntu:~$ sudo
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x375a8313

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           11996       14593    20868435    7  HPFS/NTFS






Any help would be greatly appreciated!! 

*quick note, I dont care about any of the data on the HD, just want to format and get on with Dual Booting XP and Ubuntu!!!

---

### Post by srs5694 on 2010-03-17
You appear to have one NTFS partition that covers the entire hard disk. I have two hypotheses about what may have happened:


[list=1]
[*]You may have created partitions in GParted or some similar utility but then didn't save your changes. When you started the Windows installer, it then saw an unpartitioned disk and, without making it clear to you what it was doing, it created that one NTFS partition.
[*]You attempted to create your partitions in GParted, but because of a bug or some other problem, they didn't "take," with much the same result as in hypothesis #1. I only mention this as a separate hypothesis because you mention some errors reported by (Windows? Or was this a Linux tool?) Disk Utility.
[/list]


My suggestion for how to proceed is to use Linux's fdisk. It's not as flashy as GUI tools, but it's pretty easy to use. Type "?" for a summary of commands. Create partitions as follows:


[list]
[*]A primary partition for Windows, of whatever size you desire. After creating it, give it a type code of 07 with the 't' command.
[*]An extended partition that covers the rest of the disk. This will serve as a placeholder for the next (logical) partitions.
[*]A logical partition of the size desired for shared data. This can be either type 07 (for NTFS) or 0c (for FAT).
[*]A logical partition for Linux swap. Make it at least as big as the amount of RAM you've got. Give it a type code of 82.
[*]A logical partition for Linux. This should be the rest of the disk space. Leave its type code as 83. Alternatively, you can create two or more Linux partitions -- say one for the OS and one for your user data (to be mounted at /home).
[/list]


Once you've created these partitions, you can create filesystems on most of them. Use mkfs.ntfs to create NTFS, mkdosfs to create FAT (if you use FAT for the shared partition), and mkfs.ext4 to create ext4 for Linux (if you choose to use ext4fs -- there are alternatives). Use mkswap on the swap partition.

With this done, reboot and install Windows. Be sure not to let it repartition the disk; tell it to install only on the partition you prepared for it.

---

### Post by k0brakai on 2010-03-17
Thanks for your help, I managed to format to ext3 and install xp over the whole disk and will add ubuntu later on when i get time. 

Don't quite know why it wouldnt let me format whole disk to NTFS last night but hey ho. I am an ubuntu rookie, only started using about a month ago. 

Thanks again, Solved now.

---

