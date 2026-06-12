---
title: "ubiquity crashes when trying to configure partitions"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by jwfoley on 2014-05-02
I am trying to install Ubuntu 14.04 64-bit alongside the preinstalled Windows 8.1 on an HP Envy h8. I previously shrank the Windows partition and installed Ubuntu 13.10 in a new partition, but my upgrade to 14.04 aborted prematurely so I need to do a clean install.

My problem is **the partition table comes up blank on the installer ("Installation type") and the installer crashes as soon as I click "+", "-", or "Change...": **[IMG]http://i.imgur.com/86wgjpF.png[/IMG]

I have tried deleting and recreating the old Ubuntu 13.10 partition, or just leaving it deleted, but neither of those fixes the problem. parted etc. can read the partition table just fine:

```
Model: ATA ST2000DM001-9YN1 (scsi)Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  1074MB  1073MB  ntfs         Basic data partition  hidden, diag
 2      1074MB  1451MB  377MB   fat32        EFI system partition  boot
 3      1585MB  1678GB  1677GB  ntfs         Basic data partition  msftdata
 4      1678GB  1947GB  269GB   ext4
 5      1947GB  1979GB  32.2GB  ntfs         Basic data partition  msftdata
 6      1979GB  2000GB  20.9GB  ntfs         Basic data partition  hidden, msftdata

```

(Partition 4 is the one where I had successfully installed Ubuntu 13.10 before, and then deleted and recreated the partition)

So clearly there's a bug in ubiquity, but how do I work around it? Could there be something about my partition table that it's not expecting?

---

### Post by rooker2 on 2014-05-17
Trying to install Xubuntu 14.04 on an older Dell P4 3.4 GHz. I'm having the exact same problem: Live distro boots fine, but the partitioning tool shows no drives. 

When I click on any of the "+/-/change" buttons, the installer just exits.  
I've tried running ubiquity with debug options "-d" and "--pdb" from a shell, but there was no additional output/information.   

I've also browsed the log in /var/log/installer/debug, but couldn't find what was causing the problem.  

Something worth mentioning is, that the disk I'm trying to install to was previously used with a Promise SATA RAID controller in a stripe array. It seems that there are some leftovers of that on the disk, since "cfdisk /dev/sda" showed a partition of type "promisestripe_fast". I've used cfdisk to remove that partition and re-create one, but ubiquity still won't show the disk :(

---

### Post by oldfred on 2014-05-17
@rooker2
Your issue is RAID related, and not like the OP.
 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

@jwfoley
Be very careful on reinstall. Like you have been doing only use Something Else. Those that have used the auto reinstall say it sees a previous Ubuntu install and will overwrite that and they go ahead. But it totally erases drive. See link in my signature.

Post this, to see more details
      sudo parted /dev/sda unit s print
and
      sudo gdisk -l /dev/sda
gdisk is probably not installed by default.
sudo apt-get install gdisk

---

