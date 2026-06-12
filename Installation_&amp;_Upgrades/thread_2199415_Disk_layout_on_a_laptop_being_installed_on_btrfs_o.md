---
title: "Disk layout on a laptop being installed on btrfs only."
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2014-01-13
Hi,

I am planning on installng 13.10 on btrfs only on one of my laptops. Should I partition the disk before I start with one large btrfs parition, or will the installer do it optimally if I let it use the whole unformatted disk? It says here:

[https://help.ubuntu.com/community/btrfs#Ubuntu-specific_subvolume_layout_in_11.04_and_later](https://help.ubuntu.com/community/btrfs#Ubuntu-specific_subvolume_layout_in_11.04_and_later)

<snip>
In Ubuntu 11.04 and later, the installer sets up btrfs with a specific layout:
The default subvolume to mount is always the top of the btrfs tree (subvolid=5).
Subvolumes are created below the top of the btrfs tree as needed, e.g. for / and /home, it creates subvolumes named @ and @home. This means that specific options are needed in order to mount the subvolumes, instead of the default btrfs tree top:

    The @ subvolume is mounted to / using the kernel boot option rootflags=subvol=@

    The @home subvolume (if it is used), is mounted via the mount option subvol=@home in fstab. 
</snip>

Is this what happens if I let the Ubuntu installer run autmatically on one large btrfs parition on the disk, or do I have to set the layout manually?  I want to take advantage of the cool features in btrfs one of them being easy resize so I would like to get this correct and undertand how it works. Any advice in this regard would be apprecialted.

---

### Post by oldfred on 2014-01-15
I know btrfs has some new features, but not all have been worked out yet.

 Linux 3.13 Kernel HDD File-System Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=linux_313fs_hdd&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_313fs_hdd&num=1)
10-Way Linux File-System Comparison On Linux13.10
[http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1)
BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
Linux 3.11 File-System Performance: EXT4, Btrfs, XFS, F2FS
[http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1)

---

### Post by grahammechanical on 2014-01-15
I would not confuse Btrfs volumes and sub-volumes with partitions which are sometimes called volumes in Linux. Please note this.

> [COLOR=#333333][FONT=Ubuntu]When installing Ubuntu in one large btrfs-Partition without an extra boot-partition, take care to _keep about 1 Mib space free at the beginning of the disk_. This is possible using the partition manager in the Ubuntu installer. _When there is not this space, the installer fails at the end when trying to install Grub!_[/FONT][/COLOR]

I would go so far as to say that without that minimum of unallocated free space it is impossible to use the Ubuntu installer to install Ubuntu onto a Btrfs partition. I know I tried it many times when 13.10 was under development. We get an error message that Grub failed to install. But when I created the free space at the beginning of the hard disk I was able to install Ubuntu 13.10 on a partition set to be used as btrfs.

You should also be aware that as yet we do not have a GUI snapshot manager. It all has to be done using the command line. In the software centre is a tool called apt-btrfs-snapshot. This will automatically create a snapshot every time we run the Update Manager (apt-get update) and upgrade (apt-get upgrade). For some reason the tool creates four snapshots every time. With apt-btrfs-snapshot installed then we get an additional option to the Recovery menu. Once we put the file system into read/write mode (such as running the Network option or using a command) then we will get "apt-snapshot - revert to old snapshot & reboot" as a recovery menu option. This can be very useful.

Regards.

---

