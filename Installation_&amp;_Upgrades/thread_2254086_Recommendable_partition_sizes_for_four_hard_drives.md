---
title: "Recommendable partition sizes for four hard drives?"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2014-11-25
I am currently considering a rebuild of my hybrid LinUX box in an Everex® TC2502 case definitely for multiple SATA hard drives, possibly for Intel® CPU and chipset augmented with a recently-purchased AMD® HD&#8482; 5450 PCIe x16 video card.  The current set-up with a Gigabyte® GA-MA78GM-S2HP (Advanced Micro Devices® Athlon 64® X2 5600+), which happens to already support SATA for 5*max* devices, is getting difficult to support with a fix CPU, as of 24 November 2014, as Socket AM2/+ CPUs are all discontinued and a Socket AM3 CPU will force a BIOS upgrade.  The ASRock® Z68 Pro3-M, a Micro-ATX 'board, will take my existing Creative Laboratories® SB0350 PCI audio card and recently-purchased Diamond Multimedia® A5450PE31G PCIe x16 video card; I planned on an Intel® Core Processor&#8482; i5- or i7-2*nnn* MPU or i5- or i7-3*nnn* APU (both FCLGA 1155) and four 2 GB modules DDR3-1333 SDRAM (preferably unregistered ECC, which Intel Corporation claims that the MPU/APU series under consideration will support).

I have found a near-ideal hard drive to purchase in quadruplicate and custom-shock-mount into the TC2502 case's four internal bays:  The Western Digital® WD7500BFCX Scorpio Red®, which is rated to 60°C safe operating temperature, important in my situation as I have a non-air-conditioned room pushing component choices - a Central Valley (CA, USA) summer can occasionally push ambient temperatures to on or around 40°C.  I previously installed an Antec® Tri-Cool&#8482; dual-ball-bearing fan to pull cooling air across my existing PATA drives; the WD7500's will supersede the pre-existing Hitachi® and Fujitsu® PATA hard drives, and I already have a SATA optical drive installed (the Z68 Pro3-M can reuse this).

For a custom install of Ubuntu® 14.04.*n*-LTS or (in the event of major delays) 16.04-LTS, I anticipate needing two to four 2 GB swap partitions (ext4) and ext4 partitions for /boot (528*max* MiB), /, /usr, /opt, /var, /tmp, and /srv, with preferrably a Sun Microsystems® ZFS partition (ext4 fallback) for /home.  Excepting /home (I could potentially use one entire hard drive), /boot and the previously-mentioned swaps, what partition sizes would be needed to comfortably house all Packages expected to be available for 14.04.2-LTS?

---

### Post by oldfred on 2014-11-25
Is this a server? With drives in a RAID or other special configuration. Or just 4 drives?

If a desktop I suggest / (root) of 25GB including /home. My systems uses about 11GB, and 2GB of that is /home. And my /home is only that large because I have .wine with Picasa.
But only you know what you may install in the way of applications.

Why ZFS? Do not know much about it, but prefer well supported systems.
I gather it cannot be part of standard Linux kernel & you have to recompile your own or use something else.
[https://wiki.archlinux.org/index.php/ZFS](https://wiki.archlinux.org/index.php/ZFS)
[http://www.phoronix.com/scan.php?page=news_item&px=MTc4NTM](http://www.phoronix.com/scan.php?page=news_item&px=MTc4NTM)


 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

My new system uses a SSD as boot drive and hard drive for data. But I do not have a lot of data and only allocated part of the 1TB for data. I will be installing test install(s) in 25GB / partitions.

---

### Post by bcschmerker on 2014-11-26
ZFS was initially under consideration for /home, as it acts as a RAID 1 at the disc-data level, running mirrored partitions at one mount point; the WD7500BFCX has plenty of space for such even with large user video libraries.  I chose ext4 for fallback, as it has proven its reliability in my existing 12.04.5-LTS installation.  Both the current and upgrade mobo's support five SATA devices per each, and 750 GB was the smallest capacity I could find that met my operating-temperature-range requirement.

Even with desktops I demand server file structure.  I anticipate putting /boot, / and /usr on sda; /var and /tmp on sdb; /opt and /srv on sdc; and /home on sdd, with the optical drive as sde.  My partition-sizing plan would be based on the likely sizes of the installed files in all listed Packages for 14.04.*n*-LTS at the Ubuntu® Repositories as of a given date.  Preliminary sizing plans would easily accommodate duplicate rescue partitions across four drives, much as they would accommodate parallel swap partitions across all drives.  The Grand Unified Bootloader 1.9*n*, which will be installed at sda1, can be configured to fail over to each rescue partition in turn in the event of an OS bork.

---

### Post by mastablasta on 2014-11-26
> **oldfred said:**
> 
Why ZFS? Do not know much about it, but prefer well supported systems.
.

from wiki
> The features of ZFS include protection against data corruption, support for high storage capacities, efficient data compression, integration of the concepts of filesystem and volume management, snapshots and copy-on-write clones, continuous integrity checking and automatic repair, RAID-Z and native NFSv4 ACLs.

it's kind of standard on BSD.

Linux has similar file system BTRFS which is slowly finding it's way into stable distros. next RHEL might have it. SUSE is already using it.

to the OP - you talk about disks but haven't explained what you are trying to do what is your goal. at the moment it seems the goal is "let's just make it unnecessarily complicated"

and yes the main question  - is this a server or desktop PC?

I have server on an 8 GB USB key. / is taking up the whole USB, 2GB /var/log  and 2GB /swap is on disk drive. and that's it. swap was never even used. /data is also on hard disks in software RAID1 and that's where the data is being collected. if I had the money for another hard disk I would porbably run / on one and /data on another.

if ZFS is a must requirement I suggest looking into BSD based OS such as PC BSD, FreeBSD and maybe even FreeNAS (if this is to become a data server).

---

### Post by mastablasta on 2014-11-26
raid is not a backup plan. raid is for redundancy.

---

### Post by bcschmerker on 2014-11-27
> **mastablasta said:**
> from wiki


...Linux has similar file system BTRFS which is slowly finding it's way into stable distros. next RHEL might have it. SUSE is already using it.

to the OP - you talk about disks but haven't explained what you are trying to do what is your goal. at the moment it seems the goal is "let's just make it unnecessarily complicated"

and yes the main question  - is this a server or desktop PC?

I have server on an 8 GB USB key. / is taking up the whole USB, 2GB /var/log  and 2GB /swap is on disk drive. and that's it. swap was never even used. /data is also on hard disks in software RAID1 and that's where the data is being collected. if I had the money for another hard disk I would porbably run / on one and /data on another.

if ZFS is a must requirement I suggest looking into BSD based OS such as PC BSD, FreeBSD and maybe even FreeNAS (if this is to become a data server).

It appears that the B-Tree File System, developed by Oracle Corporation among others, is close enough to a ZFS workalike to warrant consideration for the /home partition, and apparently the developers have software available to transfer directories from an ext4 volume during BTrFS installation; the WD7500BFCX is easily large enough to handle a few large BTrFS mount points.  What factor of performance hit would BTrFS entail, vs. ext4?  Although the 12.04.5-LTS box is performing desktop duty, I have to build it to server specifications due to a hostile environment; most desktop drives are not built to survive hot summers in the absence of air conditioning.

I originally planned on multiple drives of scaled capacities for the least possible performance hit during routine disc operations, as LinUX services several main subdirectories in parallel.  My 12.04.5-LTS installation, as of November 2014, is currently on two PATA drives, a Seagate® ST380215A (/dev/hda) packing the System side of the installation in one primary (/boot, at hda1) and four extended (at hda5 through hda8) Partitions, and a Fujitsu® MPC3043A serving as /home (hdb1).  I found the need for a larger /home than possible on the MPC3043A with multiple failed attempts to download DVD .iso images.  Although the GH41N optical drive (sr0) can handle some backup/restore duties, I have not found much available in terms of a SATA DAT72 transport.  The WD7500BFCX's anticipated excess capacity even with an all-BTrFS installation will allow downscaling to three hard drives to accommodate a SATA DAT72 transport, provided the latter is available; the Z68 Pro3-M has no PATA port, unlike the GA-MA78GM-S2HP.

---

### Post by mastablasta on 2014-11-27
> **bcschmerker said:**
>  What factor of performance hit would BTrFS entail, vs. ext4?

I wouldn't know that. I just read a couple of reviews and it seems that it is slightly smaller than ZFS. it is not compare much to ext4.
> 
  Although the 12.04.5-LTS box is performing desktop duty, I have to build it to server specifications due to a hostile environment; most desktop drives are not built to survive hot summers in the absence of air conditioning.


ok now that makes a bit more sense. but for disk failures you need redundancy (raid) and good backups (if possible offsite) not multiple partition. Partitioning excessively won't save the data. good backups possibly (if necessary) with OS images will. restore would then be but a click away...

I am not sure if it would apply for your case, but while I was searching for NAs there were these relatively cheap NAS devices that had fire & water protection. they cost around 400 or 500 USD. I am thinking that they might protect the disks from heat as well with some proper cooling. perhaps even external drives for backup (the small portable ones) might handle your conditions. they are low powered and probably generate less heat. another option but a lot more expencive would be SSD. they shouldn't heat up much since they have no moving parts.

perhaps they also sell more rugged drives. and usually computer boxes have their own cooling. how is that handled then?

in Linux system install is so easy that mostly I do not have system backups. I will image the server as soon a si finish the setup, but the desktop is just so easy and fast to reinstall that it Is not worth the effort to keep the system itself backed up. now prescious data is another thing...

---

### Post by bcschmerker on 2014-11-28
Thus my question concerning DAT72 tape transports.  As of 27 November 2014 I do not know whether the DAT72 requirement will force SCSI; and if so, whether a PCIe x1 host adapter is available for either U/320 or SAS.  (A retrofit video display adapter from Diamond Multimedia is tying up the x16 slot on the GA-MA78GM-S2HP and, I estimate, would do likewise on the Z68 Pro3-M.)

---

