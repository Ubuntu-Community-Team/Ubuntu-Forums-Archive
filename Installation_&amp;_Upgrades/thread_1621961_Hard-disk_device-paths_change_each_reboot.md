---
title: "Hard-disk device-paths change each reboot"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by thecabinet on 2010-11-14
For the last few days I've been trying to setup a new server running 64-bit desktop Ubuntu 10.10.  Every time the computer is rebooted, the hard disk paths (/dev/sda, /dev/sdb, etc.) change to one of two assignments.  I've twiddled various BIOS settings, none of which make any difference that I can tell.  It seems to be random which of the two assignments is chosen, but there are consistently only two.

The box has 7 hard drives.  There are 4x nearly identical 400GB drives (2x PATA and 2x SATA), and 3x identical 2TB drives.  The motherboard is an ASUS M4A785-M.  All the drives are using the motherboard's onboard SATA ports.

One set of assignments looks like:
```

root@server:~# fdisk -cul | grep -i -e disk -e dev -e '^$'

Disk /dev/sda: 400.1 GB, 400088457216 bytes
Disk identifier: 0x000b556d
   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
Disk identifier: 0x56870040
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
Disk identifier: 0x000769cf
   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 400.1 GB, 400088457216 bytes
Disk identifier: 0x00038e47
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048      999423      498688   83  Linux
/dev/sdd2          999424   765421567   382211072   83  Linux
/dev/sdd3       765421568   781422591     8000512   82  Linux swap / Solaris

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
Disk identifier: 0x1f3a7538
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdf: 400.1 GB, 400088457216 bytes
Disk identifier: 0x0001d258
   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
Disk identifier: 0xdb9a2603
   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907029167  1953513560   83  Linux

```And the other looks like:
```

root@server:~# fdisk -cul | grep -i -e disk -e dev -e '^$'

Disk /dev/sda: 400.1 GB, 400088457216 bytes
 Disk identifier: 0x00038e47
    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *        2048      999423      498688   83  Linux
 /dev/sda2          999424   765421567   382211072   83  Linux
 /dev/sda3       765421568   781422591     8000512   82  Linux swap / Solaris
 
 Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
 Disk identifier: 0x1f3a7538
    Device Boot      Start         End      Blocks   Id  System
 /dev/sdb1            2048  3907029167  1953513560   83  Linux
 
 Disk /dev/sdc: 400.1 GB, 400088457216 bytes
 Disk identifier: 0x0001d258
    Device Boot      Start         End      Blocks   Id  System
 
 Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
 Disk identifier: 0xdb9a2603
    Device Boot      Start         End      Blocks   Id  System
 /dev/sdd1            2048  3907029167  1953513560   83  Linux
 
Disk /dev/sde: 400.1 GB, 400088457216 bytes
Disk identifier: 0x000b556d
   Device Boot      Start         End      Blocks   Id  System
 
Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
Disk identifier: 0x56870040
   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907029167  1953513560   83  Linux

Disk /dev/sdf: 400.1 GB, 400088457216 bytes
Disk identifier: 0x000769cf
   Device Boot      Start         End      Blocks   Id  System

```I noticed that the devices aren't listed in order (sdf comes after sdg) but I'm not sure if that's unusual or not.

Here's the output from blkid, if that's relevant (in the first configuration).
```

/dev/sda: UUID="5757bc13-01cf-c15b-f213-6d9a31f9d279" TYPE="linux_raid_member" 
/dev/sdc1: UUID="8afe42ae-2bde-47a3-97c1-f45e3e4e348a" UUID_SUB="c0fe6ef0-3e0e-4b82-989f-c4ea0fe4b74f" TYPE="btrfs" 
/dev/sdb: TYPE="zfs" 
/dev/sdd1: UUID="47ed0671-ea5c-48d2-b0c5-b0d3ea601c41" TYPE="ext2" 
/dev/sdd2: UUID="384cb7b8-5c59-4d39-9231-32b3a4d8fdb6" TYPE="ext4" 
/dev/sdd3: UUID="df60fb6c-8d47-4f1c-968b-1de8260832fd" TYPE="swap" 
/dev/sde1: UUID="8afe42ae-2bde-47a3-97c1-f45e3e4e348a" UUID_SUB="f5f2ea00-66a3-44e9-ac02-675d932c8f17" TYPE="btrfs" 
/dev/sdf: TYPE="zfs" 
/dev/sdg1: UUID="8afe42ae-2bde-47a3-97c1-f45e3e4e348a" UUID_SUB="38f72d0c-e7b2-49c3-8763-43a7c98755ad" TYPE="btrfs" 

```I was finally able to get the box to boot reliably once I specified /boot using the UUID instead of the device:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=384cb7b8-5c59-4d39-9231-32b3a4d8fdb6 /               ext4    errors=remount-ro 0       1
# As created by Ubuntu 10.10 installer:
#/dev/sda1       /boot           ext2    defaults        0       2
UUID=47ed0671-ea5c-48d2-b0c5-b0d3ea601c41 /boot           ext2    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=df60fb6c-8d47-4f1c-968b-1de8260832fd none            swap    sw              0       0

```I don't know if it's related or not, but the 2TB drives are part of a btrfs pool (or whatever it's called).  I always have to mount that manually because (a) the mount command only succeeds with one of the three drives (not sure which one) and (b) trying to mount by UUID never chooses the right one.

FWIW, I think this is a Linux problem (rather than a BIOS problem) because the box does reliably try to boot (off the disk specified in the BIOS), and it's during the Linux boot process it will fail because /boot is /dev/sdd1 instead of /dev/sda1.

**Update**: I did some experimenting with the 32-bit desktop ISO, and it exhibits the same problem of two sets of hard-disk device paths.  So it seems to not be an issue with the 64-bit build, although that doesn't really help explain the craziness.

---

### Post by thecabinet on 2010-11-16
Sorry to bump my own post, but I'm sort of at a loss here.  Any ideas?

---

### Post by thecabinet on 2010-11-20
I eventually got around to trying Fedora, and neither 13 or 14 exhibits this problem.  Oh well; bye bye Ubuntu.

---

### Post by wedge1 on 2010-12-12
I'm having the exact same problem, I'm also on 10.10 64-bit.  I've got three different drive types.  But, I've got the same motherboard. I'm using an M4A785-V, which is the full-ATX version while the -M is the uATX.
Any clues?

---

### Post by dabl on 2010-12-12
You need to mount the drives/partitions "by-uuid", in /etc/fstab.  Then they don't change.

For example:


```
UUID=31c31df6-b090-43e9-8826-8513fd876370     /                    ext4       defaults,noatime,errors=remount-ro,barrier=0,discard,commit=300 0 1
UUID=8cee8dd4-94c1-4949-ae5e-5a7f065b0306     none                 swap       sw 0 0
UUID=ec21f5b3-7fd4-4f4b-af8d-cf787b147ae8     /mnt/REVODATA        ext4       auto,users,rw,exec,noatime,barrier=0,discard,commit=300 0 2
UUID=97ff1207-32a4-4856-b1a4-fc4eb87b7b97     /boot                ext4       defaults,noatime,errors=remount-ro,barrier=0,commit=300 0 0
UUID=9f1a991c-6ad6-40af-ba59-c10638a211c5     /mnt/WHATEVER        ext4       auto,users,rw,exec,noatime,commit=300 0 2
UUID=8206cc53-cf7d-4fa1-a62f-b358aedc8658     /mnt/DATA            btrfs      defaults 0 2
```

---

### Post by wedge1 on 2010-12-13
Yup, I've got it working now.  Thanks!

---

### Post by Frunktz on 2011-01-11
> **dabl said:**
> You need to mount the drives/partitions "by-uuid", in /etc/fstab.  Then they don't change.

For example:


```
UUID=31c31df6-b090-43e9-8826-8513fd876370     /                    ext4       defaults,noatime,errors=remount-ro,barrier=0,discard,commit=300 0 1
UUID=8cee8dd4-94c1-4949-ae5e-5a7f065b0306     none                 swap       sw 0 0
UUID=ec21f5b3-7fd4-4f4b-af8d-cf787b147ae8     /mnt/REVODATA        ext4       auto,users,rw,exec,noatime,barrier=0,discard,commit=300 0 2
UUID=97ff1207-32a4-4856-b1a4-fc4eb87b7b97     /boot                ext4       defaults,noatime,errors=remount-ro,barrier=0,commit=300 0 0
UUID=9f1a991c-6ad6-40af-ba59-c10638a211c5     /mnt/WHATEVER        ext4       auto,users,rw,exec,noatime,commit=300 0 2
UUID=8206cc53-cf7d-4fa1-a62f-b358aedc8658     /mnt/DATA            btrfs      defaults 0 2
```


I've the same problem..I resolved partially using UUID in /etc/fstab, but I have some script that need to know the exact disk (example for backup: umount and remount device), or again, a script that check some HDD params (like hddtemp or smartctl)

How I can prevent the "letter reassignment" on each boot?

Thanks

---

### Post by Azyx on 2011-02-19
> **dabl said:**
> You need to mount the drives/partitions "by-uuid", in /etc/fstab.  Then they don't change.

For example:


```
UUID=31c31df6-b090-43e9-8826-8513fd876370     /                    ext4       defaults,noatime,errors=remount-ro,barrier=0,discard,commit=300 0 1
UUID=8cee8dd4-94c1-4949-ae5e-5a7f065b0306     none                 swap       sw 0 0
UUID=ec21f5b3-7fd4-4f4b-af8d-cf787b147ae8     /mnt/REVODATA        ext4       auto,users,rw,exec,noatime,barrier=0,discard,commit=300 0 2
UUID=97ff1207-32a4-4856-b1a4-fc4eb87b7b97     /boot                ext4       defaults,noatime,errors=remount-ro,barrier=0,commit=300 0 0
UUID=9f1a991c-6ad6-40af-ba59-c10638a211c5     /mnt/WHATEVER        ext4       auto,users,rw,exec,noatime,commit=300 0 2
UUID=8206cc53-cf7d-4fa1-a62f-b358aedc8658     /mnt/DATA            btrfs      defaults 0 2
```


How do I do thaT if I have zfs-disks, that are not mounted i fstab?

/Cheers

---

### Post by gratou on 2011-03-14
> **Azyx said:**
> How do I do thaT if I have zfs-disks, that are not mounted i fstab?

/Cheers

Same problem here with 10.04.

The zfs pool references sda to sdd, but the disks sometimes connect as something else and the pool is unavailable.

what should i do? thx a lot.

---

### Post by atcrank on 2011-09-19
Hi all,

Hope this thread isn't too stale - has anyone tried the bios upgrades?  The latest is issued around the time this thread finished (18 Mar 2011). 'Fix stability issues' or 'Add CPU support' is all Asus will say, which is not helping. Stability was fine.

I am having the exact same issue, M3-785T-M, mix of drives (160GB Hitachi 2.5", WD 1TB Green, 640Blue, Samsung 640).  My Mythtv(!) drive won't mound because its suddenly sdd instead of sdb.


Andrew

---

### Post by mszmansky on 2012-03-14
I have upgraded my ubuntu 64 bit server install to the latest oneiric version 11.10 and this issue keeps happening.  When I reboot, all 5 of my hard drivs get assigned different dev letters.  I cannot keep my RAID configuration between boots. I have to manually redo the arrays every time I reboot.  Is there any way to prevent Ubuntu from reassigning my hard drive letters?

---

### Post by Azyx on 2012-03-14
If you make ```
sudo blkid
``` in terminal you get a blockid for your partitions. Use that instead of /dev/sdx in fstab. Works if you have partition as in most filesystem. It may be problem in zfs, there the system don't have any partition.

In terminal run:

```
Azyx@Intel:~$ sudo blkid
[sudo] password for a: 
/dev/sda1: UUID="3d23a87e-9990-407c-b71f-3a7f1b54368e" TYPE="swap" 
/dev/sda5: UUID="bc85cb3c-babd-4274-a0e4-364ae16e5d8b" TYPE="ext4" 
/dev/sda6: UUID="d7905cf0-f03d-423c-a3c3-ac1fe05c15e3" TYPE="ext4" 
```

Then the open fstab with for example: sudo nano ```
/etc/fstab
``` and replace the /dev/sdx in /etc/fstab so it look like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=bc85cb3c-babd-4274-a0e4-364ae16e5d8b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=d7905cf0-f03d-423c-a3c3-ac1fe05c15e3 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=3d23a87e-9990-407c-b71f-3a7f1b54368e none            swap    sw              0       0
```

PS. See that sudo blkid gives "-sign before and after the id, so you need to remove them in fstab.

---

### Post by zertoss on 2012-04-08
@mszmansky,
I had this same issue a week ago.
Managed to fix it by changing the mdadm config file /etc/mdadm/mdadm.conf to use:
```
DEVICE /dev/sd*
```

Instead of the default:
```
DEVICE partitions
```


My mdadm.conf file looks like this:
```
DEVICE /dev/sd*
ARRAY /dev/md0 UUID=05c72321:0c38161d:3cf42320:19b0e985
```

Assuming all your hard disks are assigned some sort of /dev/sd*  device name, mdadm will scan all devices matching those names and look for the array UUID then assemble the raid base on the UUID, the raid information itself is stored in the super-block of the hdd's so you don't need to worry about the details of how to assemble the array, like raid levels, number of devices etc..

Just examine one of the hard disk's which is part of an array and you'll see the super-block containing all the information needed for mdadm to reassemble the array.
e.g. If /dev/sdb1 is part of an array run this to see the super-block information:

```
mdadm --examine /dev/sdb1
```

I worked all this out by reading a tonne of information on mdadm.
[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)
[http://linux.die.net/man/5/mdadm.conf](http://linux.die.net/man/5/mdadm.conf)


Side tip: When first creating a raid1 or raid 10, you don't need to wait for the raid array to "resync" as part of the array initialization which depending on the HDD size can take up to 48 hr!!
Use the "--assume-clean" options. See the references above.
Also if you want to speed up resyncing, follow these steps:
[http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html](http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html)

Good luck.  :p

---

### Post by recluce on 2012-04-08
Additional tip: don't use FUSE-ZFS. It is outdated, very slow and extremely unreliable. 

For example: in my tests FUSE-ZFS decided to use a device just inserted into an eSATA dock as its new SPARE, forgetting about the existing one - and overwriting the MBR and partition table of the external drive!

ZFS is sweet, but unfortunately it is not well implemented on Linux at this point in time. Either use a Linux software RAID or switch to FreeBSD, if you want to use ZFS.

---

