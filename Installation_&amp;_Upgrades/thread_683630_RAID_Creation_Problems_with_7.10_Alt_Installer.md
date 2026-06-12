---
title: "RAID Creation Problems with 7.10 Alt Installer"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by flamsmark on 2008-01-31
I'm trying to install 7.10 on a couple of RAID arrays with the alternate installer (text mode). However, partman, the partitioner, seems to want to make arrays for me, and won't let me delete them.

I have five disks attached to this machine:
- a 40gb IDE drive connected to the motherboard
- a 160gb SATA drive connected to the motherboard
- three 300gb SATA drives connected to a Highpoint RocketRAID controller
- a 320gb SATA drive connected to the same controller

The controller mentioned above doesn't actually seem to be a RAID controller, just a SATA controller. The installer sees the disks attached to it, not arrays that I've created with it. I'm disappointed, but dealing with it by making software raid arrays with the installer.

I started up the alt disk, went to a virtual console, and used dd to write urandom over the first 512mb of each of the disks. Then, I rebooted, and made my way to the partitioner. I partitioned my disks as follows:

```

IDE1 master (hda) - 300.1 GB Maxtor 6V300F0
     #1 primary 300.1 GB    K  raid
IDE2 master (hdc) - 320.1 GB MAXTOR STM3320820AS
     #1 primary 300.1 GB    K  raid
     #2 primary  20.1 GB    K  raid
IDE3 master (hde) - 300.1 GB Maxtor 6V300F0
     #1 primary 300.1 GB    K  raid
IDE4 master (hde) - 300.1 GB Maxtor 6V300F0
     #1 primary 300.1 GB    K  raid
SCS1 (0,1,0) (sda) - 40.0 GB ATA WDC WD400AB-00CM
     #1 primary 255.0 MB  B F ext3            /boot
     #3 primary  19.8 GB    K raid
     #2 primary  20.0 GB    K raid
SCS1 (0,1,0) (sda) - 160.0 GB ATA WDC WD1600JD-75H
     #3 primary 120.2 GB    K crypto         not active
     #2 primary  19.8 GB    K raid
     #1 primary  20.0 GB    K raid

```

My intention was to make:
- a 900GB RAID5 for /var/files with hda1, hdc1, hde1 and hdg1
- a 40GB RAID0 for / and swap with sda2 and sdb2
- a 40GB RAID5 to be used a backup for the array above using hdc2, sda2 and sdb1
- a random 120GB partition out of sdb3

When I went to Configure Software RAID>Create MD device, I find that only hdc1, hdc, sda3, sda2 and sdb2 are available for use. If I go to Delete MD device, I find the following devices:

```

md1
:
inactive
sdb1[2]
md0_raid5

```

Looking closer, I am informed that 'md1' has component devices 'inactive sdb1[2]'; ':', 'inactive', and 'sdb1[2]' don't seem to do anything; and 'md0_raid5' has component devices 'hda1[0] hdg1[3] hde1[2]'. However, I can't delete any of these devices when I try.

Returning to the paritioner, I find the new entry:

```

RAID5 device #0 - 900.2 GB Software RAID device
        #1 900.2 GB

```



What's going on here? Am I doing something wrong? Is there something squiffy with my disks? Is there something wrong with my installer?

I am completely stumped, especially by how a 900GB RAID5 array can be made with 3 300GB partitions.

Any help would be much appreciated.

---

