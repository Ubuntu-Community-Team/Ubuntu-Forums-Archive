---
title: "Install issues - Ubuntu will not boot"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by ukch on 2005-05-02
Hi,

I downloaded the Hoary ISO image, checksummed it and it came out ok.

I have a 40GB hard disk. My partitions are as follows:

27GB Windows NTFS Partition (bootable)
1GB FAT32 Partition
1GB Linux EXT3 Partition (mounted as /)
9GB LVM, of which:

1GB formatted as Swap
2GB EXT3 (/home)
3.5GB EXT3 (/usr)
2GB EXT3 (/opt)

The installation went fine up until it got to configuring APT, at which point it froze while trying to test the network.

I decided to skip this step and move straight on to installing GRUB. I tried installing both in the MBR and on my root partition (hd0,2). Both failed with an error about /boot/grub/stage1, which I have checked and is fine.

At this point, I decided to switch to the console and run grub to see what the problem might be. GRUB could not read my partition at all. It gave me the error: 'unknown file type'. I decided to reboot and see if my current version of GRUB would work (I have previously used Debian Sarge), and that exited with the same error. I have checked the CD again and it is fine. Can anyone help me?

---

### Post by ukch on 2005-05-02
Oops. Just noticed I have posted this in the wrong forum!

Please see [http://www.ubuntuforums.org/showthread.php?t=31306](http://www.ubuntuforums.org/showthread.php?t=31306)

---

