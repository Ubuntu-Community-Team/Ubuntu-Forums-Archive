---
title: "Ubuntu 14.04 not booting, dropping to BusyBox (initramfs)"
date: 2015-12-11
forum: Installation &amp; Upgrades
---

### Post by PaulRSte on 2015-12-11
After a power supply failure which also took out the motherboard, I have just got round to also replacing the motherboard, memory, and processor. New kit is an Asus M5A78L-M/USB3 with an AMD FX4300 Black Edition Quad Core processor, and 8GB HyperX Memory. Cooling is via a ThermalRight AXP-200R. The add-in cards from the old mother board are still working and are an Nvidia Graphics Card, Hauppauge twin tuner card, and additional ASUS Optical Out card which connects to a header on the motherboard (so I can connect the digital coax connector to the surround sound receiver).

Initially the system was connected to a normal PC monitor and all went well powering it up. After spending an hour auto checking the original hard drives - all OK -  and the better part of 2 hours installing software updates it seemed to be working well so it was reconnected to our TV.  Two days later and it has crashed again.

I have two 500GB disks with identical partition layouts which are (approximate sizes), in sequence:-
50GB Boot partition
5GB Swap Partition
12GB Home Partition
440GB Recordings Partition

The two Boot Partitions and the two Home Partitions run as software Raid 1 (Mirror)
The two recordings partitions are non RAID for MythTV (Recordings and Recordings2) which balances the load between them.

The fault started sometime during the night.  Something was wrong but I wasn't sure what but it seemed that a reboot was in order.

On rebooting it reported that the Recordings  partition could not be mounted and offered Skip or Manual mount options. After shutting down and rebooting I then noticed that the Recordings2 partition was not being mounted either. In retrospect though, I believe that the mount point for this is in the Recordings folder, which would obviously prevent the second one being mounted as well.

A further problem is that having skipped both recordings partitions to allow the boot to continue, the system came up with a smaller than usual screen size and a report that suitable parameters could not be found.

Having booted from the 14.04 LTS boot DVD (screen size normal) I ran GParted and did a check on all the partitions. All seemed to be ok but on rebooting it is now dropping to BusyBox (initramfs). If I exit out of this it displays a trace and then hangs.

Can anyone offer some help on how to progress this please.  I have run the following commands having seen this as a starting point for a similar fault.


```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d09e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    97659134    48829536   fd  Linux raid autodetect
/dev/sda2        97659135   109659689     6000277+  82  Linux swap / Solaris
/dev/sda3       109659690   133644734    11992522+  fd  Linux raid autodetect
/dev/sda4       133644735   976768064   421561665   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc53c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    97659134    48829536   fd  Linux raid autodetect
/dev/sdb2        97659135   109659689     6000277+  82  Linux swap / Solaris
/dev/sdb3       109659690   133644734    11992522+  fd  Linux raid autodetect
/dev/sdb4       133644735   976768064   421561665   83  Linux

Disk /dev/sdc: 7864 MB, 7864320000 bytes
255 heads, 63 sectors/track, 956 cylinders, total 15360000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x092b268b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    15359999     7678976    b  W95 FAT32
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA HDS725050KLA360 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  50.0GB  50.0GB  primary  ext3            boot, raid
 2      50.0GB  56.1GB  6144MB  primary  linux-swap(v1)
 3      56.1GB  68.4GB  12.3GB  primary  ext3            raid
 4      68.4GB  500GB   432GB   primary  xfs


Model: ATA HDS725050KLA360 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  50.0GB  50.0GB  primary  ext3            boot, raid
 2      50.0GB  56.1GB  6144MB  primary  linux-swap(v1)
 3      56.1GB  68.4GB  12.3GB  primary  ext3            raid
 4      68.4GB  500GB   432GB   primary  xfs


Model:   (scsi)
Disk /dev/sdc: 7864MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7864MB  7863MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: Optiarc DVD RW AD-7173A (scsi)
Disk /dev/sr0: 4706MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3979MB  3989MB  9568kB               EFI


ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="a413a2f7-07d5-a6d8-915d-4e9b9f101203" TYPE="linux_raid_member" 
/dev/sda2: UUID="20aa22cf-da00-4e46-a279-0a161278c129" TYPE="swap" 
/dev/sda3: UUID="432486f1-99b1-33aa-915d-4e9b9f101203" TYPE="linux_raid_member" 
/dev/sda4: UUID="12544d66-0b05-478d-84f7-88d36a6a81f1" TYPE="xfs" 
/dev/sdb1: UUID="a413a2f7-07d5-a6d8-915d-4e9b9f101203" TYPE="linux_raid_member" 
/dev/sdb2: UUID="9ee3e3de-ea36-4778-9881-b55bb7b23e47" TYPE="swap" 
/dev/sdb3: UUID="432486f1-99b1-33aa-915d-4e9b9f101203" TYPE="linux_raid_member" 
/dev/sdb4: UUID="2295357c-ddac-46a8-b551-d6fead02bb78" TYPE="xfs" 
/dev/sr0: LABEL="Ubuntu 14.04.1 LTS amd64" TYPE="iso9660" 
/dev/sdc1: LABEL="7_9GB" UUID="46F6-6084" TYPE="vfat" 
ubuntu@ubuntu:~$ gedit


```
 
Can anyone offer some help on how to progress this please.

---

### Post by T.J. on 2015-12-11
Have you tried booting the machine with a rescue disc, and then regenerating both the bootloader (*update-grub* or *grub-install*) and the initramfs (*update-initramfs -k all -u*)?  If your initrd was generated using limited drivers, it may not boot properly on your new hardware until you do.  It's also possible that your drive designations have changed.  If you need more suggestions, please feel free to post back, and I'll try to walk you through whatever you need. =) 

Have a fabulous day!

---

### Post by PaulRSte on 2015-12-12
Thanks for the update T.J.  After posting this last night I did a little investigation of the live DVD (see next paragraph).  The system had run ok for 2 days on the new hardware and had done some major updates.  The system has been down since July but has had the least priority as I've also been replacing my SBS2003 server and my XP PC with an Apple MAC.  The server has crashed as well since getting the MAC and getting the email working has been a nightmare.

One of the things I was trying to do with the HTPC was watching something from Channel Five's web site but have a huge issue with getting the Flash player updated in Firefox. This seems to be a bit of an issue generally so I loaded Firefox from the live DVD and it doesn't have any Flash player installed at all. Presumably this will be the case on a fresh install so getting the latest version of Flash should work ok. I tried to install it but it wouldn't when loaded from the live DVD. I have tried updating to the latest Flash on my system and whilst the install runs ok, Firefox still has the old version showing in add ons.

We've had a long think about it and we've decided to go for a total rebuild on new disks.  This was the ultimate plan anyway as the system is 8 years old.

Thanks again for the reply but I'm going to close this now.

---

