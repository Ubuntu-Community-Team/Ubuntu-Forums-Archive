---
title: "Migrating a ZFS root pool from BSD, how to install grub?"
date: 2017-08-04
forum: Installation &amp; Upgrades
---

### Post by rnctx on 2017-08-04
Hello guys, I'm pretty close to sorting this out but have one last hurdle I can't seem to find an answer to after a day of searching.

I have a RaidZ pool that was, as of yesterday, running FreeBSD 11.  It's a non-UEFI motherboard, which FreeBSD handles root ZFS booting of by mirroring its loader onto all of the drives in the array, like so...

```

(parted) print                                                            
Model: ATA WDC WD20EFRX-68A (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name      Flags
 1      20.5kB  545kB   524kB                gptboot1
 2      545kB   4296MB  4295MB               swap1
 3      4296MB  2000GB  1996GB  zfs          zfs0

```

That same architecture exists on every drive, sda through sdf.

Due to the deterioration of support for common things in FreeBSD and the improved support for ZFS in linux, I've decided to migrate the OS over to Ubuntu 16.04.  Initial testing with import/export of the pool show me no errors.  Ubuntu 16.04's live disk (after ZFS tools/libs are installed) reads and writes to the pool just fine.  So with that in mind I set about removing FreeBSD (by destroying the datasets containing the various BSD specific folders, leaving only my homes (that have all of my data stored) intact), making new datasets that mimic the paths Ubuntu wants, and chrooting into it to install a base system after importing the pool to an alternate mount point.  All of that is working fine. I am able to install, upgrade, and configure all of the OS's requirements.

The hangup is how to install grub.  As you can see above FreeBSD's boot loader existed on this (and my five other) drives in the first partition.  I removed that partition on each drive, along with the FreeBSD swap, and created a new partition on each drive for grub to live in, and then created a new linux-swap dataset in the array for the remaining space, like so...

```

(parted) print                                                            
Model: ATA WDC WD20EFRX-68A (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  525MB   524MB   ext2         boot  bios_grub, legacy_boot
 2      525MB   825MB   300MB   fat32            UEFI  boot, esp
 3      4296MB  2000GB  1996GB  zfs          zfs0


(parted) 
```

```

root@ubuntu:/# zfs list
NAME                USED  AVAIL  REFER  MOUNTPOINT
media              5.15T  3.27T   153K  none
media/ROOT          307K  3.27T   153K  none
media/ROOT/ubuntu   153K  3.27T   153K  /mnt
media/home         5.15T  3.27T  5.15T  /mnt/home
media/srv           153K  3.27T   153K  /mnt/srv
***media/swap         3.60G  3.27T   102K  -***
media/var          88.6M  3.27T   153K  /mnt/var
media/var/cache    84.6M  3.27T  84.6M  /mnt/var/cache
media/var/games     153K  3.27T   153K  /mnt/var/games
media/var/log      3.05M  3.27T  3.05M  /mnt/mnt/var/log
media/var/mail      198K  3.27T   198K  /mnt/var/mail
media/var/nfs       153K  3.27T   153K  /mnt/var/nfs
media/var/spool     153K  3.27T   153K  /mnt/var/spool
media/var/tmp       173K  3.27T   173K  /mnt/var/tmp
```

Since I'm monkeying with partitions I went ahead and created a blank UEFI in case I need to switch motherboards, as well.

As is the case with many users of a NAS, I don't have enough storage elsewhere to destroy the array and re-create it.  That's the purpose of a NAS, after all...

I've been following the excellent guide at [https://github.com/zfsonlinux/zfs/wiki/Ubuntu-16.04-Root-on-ZFS](https://github.com/zfsonlinux/zfs/wiki/Ubuntu-16.04-Root-on-ZFS) but that guide assumes that the user is making new pools.  I have to save my old pool in this case, as I have nowhere else to fit the data for a migration.

The only hangup is how to install grub in the chroot?

No matter what I've tried I can't get the grub installation (via apt) to see the partitions I've created....

```

root@ubuntu:/# apt install --yes grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-gfxpayload-lists
The following NEW packages will be installed:
  grub-gfxpayload-lists grub-pc
0 upgraded, 2 newly installed, 0 to remove and 83 not upgraded.
Need to get 0 B/201 kB of archives.
After this operation, 606 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package grub-gfxpayload-lists.
(Reading database ... 18256 files and directories currently installed.)
Preparing to unpack .../grub-gfxpayload-lists_0.7_amd64.deb ...
Unpacking grub-gfxpayload-lists (0.7) ...
Selecting previously unselected package grub-pc.
Preparing to unpack .../grub-pc_2.02~beta2-36ubuntu3.12_amd64.deb ...
Unpacking grub-pc (2.02~beta2-36ubuntu3.12) ...
Setting up grub-pc (2.02~beta2-36ubuntu3.12) ...


Creating config file /etc/default/grub with new version
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
Installing for i386-pc platform.
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?).
Installing for i386-pc platform.
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?).
Installing for i386-pc platform.
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?).
Installing for i386-pc platform.
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?).
Installing for i386-pc platform.
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?).
Installing for i386-pc platform.
grub-install: error: cannot find a device for /boot/grub (is /dev mounted?).
Setting up grub-gfxpayload-lists (0.7) ...
```

I tried mounting each new boot partition and reconfiguring grub for each, but that doesn't seem to make any difference.  No matter what I try, grub-probe fails...

```

root@ubuntu:/# grub-probe /
grub-probe: error: cannot find a device for / (is /dev mounted?).

```

I did bind /dev /proc and /sys to folders under my chroot mount before doing this.  I can see them in the shell, but grub's installer cannot, for some reason?

---

### Post by rnctx on 2017-08-05
I fixed this, for anyone else that might stumble across it...

The guide on the zfsonlinux Github page suggests setting the root mount with a flag of...

```

canmount=noauto

```

This works for getting everything into the chroot (NOT REALLY^) but it will not boot that way because.... derp, the root disk doesn't mount at boot.  Even if you do every step in the guide and pass the steps it says to pass in verification, the resulting system won't boot without a root / directory.

I suspect that the reason the guide was written that way is that getting a ZFS dataset that points to root to mount for chroot purposes is a bit of a chicken/egg scenario.

The reason being, zpool has the -R flag to tell a whole pool of datasets where to mount, but the zfs command (for mounting individual datasets) does not.  With the zfs command all you can do is change the mountpoint of the dataset permanently, and then (hopefully) not forget to change it back when you're done if you're using this stuff in a chroot.

I think the proper way to do this, reading around on grub's bug reports and documentation, is to unmount/remount the datasets when you've chrooted in, that way your root ( / ) actually points to ( / ) and not /mnt or /temp or some other such place.  The catch22 here is that zpool is independent of the rest of the filesystems and thus does not respect the chroot.

The problem at the end of all of this is that grub needs to see a root ( / ) device to know where the /boot folder is.  Grub has poor error handling, and will tell you that it can't find it if you're in a chroot even as it is putting files into the folder that it says it can't find.

**tl;dr(^):**

Omit the part of the guide suggesting "noauto" for the root device mount, leave it to the default which lets it automatically mount.  While following the other steps of the guide, routinely check "mount | grep zfs" to ensure that all of your zfs directories (datasets) are mounted where they should be mounted, particularly the root, before installing things or otherwise moving things around.  Unmount/remount the datasets within the chroot as necessary to accomplish this.

---

