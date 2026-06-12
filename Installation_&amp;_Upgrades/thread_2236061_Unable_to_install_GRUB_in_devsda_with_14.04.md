---
title: "Unable to install GRUB in /dev/sda with 14.04"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by windofkeltia on 2014-07-24
Attempting to install new Ubuntu 14.04 Server from fresh-burned CD off ubuntu.com. No signs of difficulty whatsoever before GRUB install. This system was brand new in January 2013 and since then ran VWware ESXi as a test server with no problems at all during installation or production. (I'm now going to make it run Plex Media server.)

i5-2500K CPU
ASUS P8Z77-V MOBO
16Gb memory
2 x WD 2Tb drives

To which I added three additional disks for this installation:
2 x Seagate 4Tb drive (brand new)
1 x Seagate 320Gb drive (what I want to be system and boot drive)

Windows, dual boot, crazy stuff __not__ part of the question here. The 320Gb drive did have NTFS on it for a couple of years, but I expected Ubuntu install adequately wiped that and see no sign it did not.

For now, I'm completely ignoring all the big drives which I plan to use zfs on later.

Of course, I googled around and systematically tried:

- enforcing suggested BIOS settings (disable secure boot, disable fast boot, couldn't find that stuff)
- installing 12.04 to see if it behaved differently (gets same error)
- exchanging 240Gb SSD for 320Gb Seagate
- boot drives partitioned afresh each trial as [boot (200-300Mb), swap (16Gb) and / (rest)]
- changing which SATA connector on MOBO used

Many thanks for reading post and profuse thanks for any answers!

---

### Post by ubfan1 on 2014-07-24
Was this a UEFI machine with Windows 8 preinstalled?  Is the disk partitioning on the boot disk gpt?  Are you trying to install in legacy mode?  If your disk is gpt, do you have a grub-bios flagged 1M partition for the boot image (which no longer fits nicely just after the boot block)?  A few more details would help in providing some suggestions.

---

### Post by Bashing-om on 2014-07-24
windofkeltia; Hello;

Raid ? .. were the disk(s) ever used in a raid array ? Is the new server to be set up using Raid ?
Are you installing from the 'server' edition, such that you have access to the Raid tools ?

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by windofkeltia on 2014-07-24
I did see UEFI in the BIOS settings, but didn't touch it. I built the machine myself, Windows was never in the mix. The disk partitioning is being done using only the Ubuntu 14.04 installation disk. I'm not super knowledgeable at this level; I haven't flagged or attempted not to flag gpt in the BIOS. I'm happy to provide more detail.

Thanks.

---

### Post by windofkeltia on 2014-07-24
I am installing an Ubuntu 14.04 LTS Server downloaded from ubuntu.com and burned on a CD, using the CD in this machine to perform all installation. None of the disks were ever used in a RAID set-up. When running ESXi, I did create some 12 separate tiny Ubuntu 12.04 servers to experiment with MongoDB and application clusters at the time (Jan 2013-July 2014) on the 2 x 2Tb drives. The 2 x 4Tb drives are brand new out of the box. The 320Gb drive I'm hoping to use for the system disk was once in a Windows machine, but was not the bootable drive there.

My plan is to set up a RAID (10--as I understand it) using zfs. I will mirror the two identical 2Tb drives, the two identical 4Tb drives, then drop both mirrored sets into a single volume. My understanding, because I've not used zfs yet, is that I can do the zfs work after installing the OS.

Thank you.

---

### Post by Bashing-om on 2014-07-24
windofkeltia; Hey,

OK, raid is not of consideration, back to ubfan1's observation -> what is the partitioning scheme on the hard drives ? It do make the difference in the booting method and as such how/where grub is installed.
Post back to us the outputs of terminal commands:
```

sudo fdisk -lu
sudo blkid
sudo parted -l

```
IF the partitioning is GPT we need a different tool to look at the scheme:
```

sudo apt-get install gdisk
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb
sudo gdisk -l /dev/sdc

```
and so on for each hard disk installed.

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by windofkeltia on 2014-07-24
I'll need a little help here.

If I'm doing a naked, from ground-up installation from a CD containing Ubuntu 4.04 Server, at what point can I get into a console to execute these commands and how do I get into that console? I know that if I'm installing desktop, it's a no-brainer to get a console (because booted from the CD itself), but server?

Thanks.

---

### Post by Bashing-om on 2014-07-24
windofkeltia; Hey,

Been ages since I boot a server disk ..
Try the F4 key .. best I recall that gets ya a terminal.

[INDENT][INDENT]I do hope that helps
[/INDENT][/INDENT]

---

### Post by windofkeltia on 2014-07-24
Thanks. That doesn't work. What I did was disconnect all disks except the one I want the system installation on and retried the installation, which worked. (Lesson learned: don't attempt a system install with a bunch of disks--although I've done this successfully before).

It's then that I was able to oblige your advice. Here is the relevant output from the above. I would like to draw your attention to "msdos" below, which concerns me. (I've bolded it and bumped its font size for this reply.) I thought the installation would wipe that drive completely before partitioning, formatting and installing. And the disk doesn't seem to pose a problem as the OS boots fine, I can log in, run these commands, etc.

Do you have any advice at this point? Note that I plan to attempt the zfs wiggle to set up the other disks. I did reconnect them and the system does boot. I ran these commands in that state, but that output isn't here. If relevant, I can give it--might be better if I serve it up as a web page though.

Thanks

$ fdisk -lu
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000146f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   625141759   312320001    5  Extended
/dev/sda5          501760   625141759   312320000   8e  Linux LVM

Disk /dev/mapper/tol--eressea--vg-root: 302.9 GB, 302946189312 bytes
255 heads, 63 sectors/track, 36831 cylinders, total 591691776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/tol--eressea--vg-swap_1: 16.8 GB, 16848519168 bytes
255 heads, 63 sectors/track, 2048 cylinders, total 32907264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

$ blkid
/dev/sda1: UUID="195fdacc-4891-4250-a901-241b655387b1" TYPE="ext2"
/dev/sda5: UUID="5JtzN6-u6QS-Nju1-uDs5-N1Ml-WGIi-PJgOcX" TYPE="LVM2_member"
/dev/mapper/tol--eressea--vg-root: UUID="359c69e9-fe56-4403-94e0-0ef569518263" TYPE="ext4"
/dev/mapper/tol--eressea--vg-swap_1: UUID="87631cc8-248e-424b-a9dd-d93ee2ec74ca" TYPE="swap"
parted -l
Model: ATA ST3320613AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
[B][SIZE=3]Partition Table: msdos
[/SIZE][/B]
Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   320GB  320GB  extended
 5      257MB   320GB  320GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/tol--eressea--vg-swap_1: 16.8GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  16.8GB  16.8GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/tol--eressea--vg-root: 303GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  303GB  303GB  ext4


$ gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory.
***************************************************************

Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 418217A9-65D7-48C6-9CC9-6C77D04F09B0
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 4717 sectors (2.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          499711   243.0 MiB   8300  Linux filesystem
   5          501760       625141759   297.9 GiB   8E00  Linux LVM

---

### Post by ubfan1 on 2014-07-24
The msdos partition type is not a problem, that is just the name given to that type of partitioning.  The Logical Vol type you selected is something I do not use, so cannot offer any advice.  If your machine is UEFI capable, you might consider using its capabilities, but if you don't care about the abiity to have multiple boot loaders, makes no difference.

---

### Post by windofkeltia on 2014-07-24
Great! No, I'm never interested in dual-booting Windows. I just wanted a vanilla Ubuntu 14.04 LTS installation. I gave Windows up nearly a decade ago. I really appreciate the two of you stepping in here. Next up will be using zfs and that's a different forum if it doesn't go well, but I think it will.

Thanks!

Russ

---

