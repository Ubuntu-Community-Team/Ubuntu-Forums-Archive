---
title: "After 9.10 upgrade, system can't load root file system"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Kickboy on 2009-11-22
This is a rather weird issue... I upgraded my 9.04 installation today to 9.10 using the network installation. Everything installed just fine, kernel updated, grub config was changed, etc. Upon rebooting, everything seems to be going smoothly until I get to the splash screen. Interestingly enough it hangs at the "Waiting for root file system..." step, then drops me to busybox prompt saying the drive /dev/disk/by-uuid/%%hash%% could not be found, even through I booted off of this very partition and it could read it just fine up until this point in the boot process.

I have tried everything I know, and done some research, but can't find anybody else with a similar issue. Should I simply have the boot option set to wait for the root file system for 5 minutes and see if it eventually finds it?

As a side note, when I boot from my GParted live CD, all the disks appear as they should be, and the UUID that throws an error on boot shows up just fine. I've checked all the drives so they do not appear corrupted.

Could this be some issue with the latest kernel installation? I attempted switching it back to 2.6.28-16 (kernel from 9.04), but had the same issue (currently kernel 2.6.31-15).

I can post by /etc/fstab and /boot/grub/menu.lst files if that would help, but there isn't anything special in them; mostly default settings.

Any help would be appreciated!

---

### Post by Kickboy on 2009-11-22
Here are some more details...

When I boot into Ubuntu 9.10 LiveCD on my system to try and inspect the hard drives, I find the GParted and e2fsck have trouble accessing the partitions now. This does not happen on the GParted LiveCD.

Here are some interesting results:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00017747

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5227    41985846   83  Linux
/dev/sda2            5228       32935   222564510   83  Linux
/dev/sda3   *       32936       38162    41985877+   7  HPFS/NTFS
/dev/sda4           38163       38913     6032407+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009eb77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

```

You'll notice I have 2 drives. The second drive (sdb1) is my /home partition (keep it separate for easy portability and OS re-installation). The main OS is /dev/sda1, sda2 is a my backup partition, and sda3 is my WinXP partition (Dual Boot).

What's interesting is even though all these partitions show up in fdisk, I can't access or view any of them.

```

ubuntu@ubuntu:~$ sudo ls /dev/sd*
/dev/sda  /dev/sdb

```

The partitions don't actually show up in dev, so I can't mount or check them.

```

ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux-ng 2.16
fsck: fsck.nvidia_raid_member: not found
fsck: Error 2 while executing fsck.nvidia_raid_member for /dev/sda

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sda
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

```

I'm at a loss. How did my partitions get so corrupted that they can't even be found? Even though I am still able to boot just fine into my XP Parition, and even access my other paritions through XP via the ext2fs windows driver. But when I try to boot into my Ubuntu 9.10 partition, it only boots part of the way and then crashes at the splash screen like I described in my previous post.

I tried running the 9.10 installation from the CD, but when I get to my partition editor, the only disk option is can find is for /dev/mapper/nvidia_cacffhcc, which is supposedly a RAID device, but I have no RAIDS configured. This is all very confusing.

Any help please? This is driving me nuts!

---

### Post by Kickboy on 2009-11-22
Mark this as SOLVED.

The problem has to do with the 9.10 upgrade causing it to "detect" a RAID automatically, completely throwing off all my partitions and causing weird errors and behaviour. It was trying to RAID my root partition (/) and my /home partition, which I have on separate drives. This cause my root partition to get completely corrupted. Luckily it didn't cause corruption on my home partition where my sensitive data is. This is exactly why I keep these partitions on separate drives.

I found instructions on how to solve this annoying issue on the following forum post, which I found after countless hours of debugging and google searches. **Solution:** [http://ubuntuforums.org/showpost.php?p=8334643&postcount=4](http://ubuntuforums.org/showpost.php?p=8334643&postcount=4)

This is a rather serious issue to have happen during an upgrade, and I seriously hope Ubuntu staff take a close look into this problem so that others don't experience the same thing. I could have easily lost all my files, and I am now (as of typing) re-installing Ubuntu from scratch via livecd since all my root system files were completely corrupted.

---

