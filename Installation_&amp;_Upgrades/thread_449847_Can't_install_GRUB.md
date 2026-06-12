---
title: "Can't install GRUB"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by kenklose on 2007-05-20
I'm trying to install Kubuntu from the live CD onto an existing Win XP system.  First I created a swap and ext2 partition using partition magic.  Then I ran the CD.  The install went fine until it tried to install GRUB (on device /dev/sda), it gave me a "fatal error".

I booted the live CD and used parted to get the following information about the disk that I am installing to:

Disk /dev/sda: 74.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number	Start	End	Size	Type	File system	Flags
1	32.3kB	63.7GB	63.7GB	primary	ntfs	hidden
3	63.7GB	65.9GB	2147MB	primary	linux-swap	
2	65.9GB	74.3GB	8497MB	primary	ext2	boot

I tried grub-install, this time to /dev/sda2 instead of /dev/sda but that didn't help:

% sudo grub-install /dev/sda2
Probing decides to guess BIOS drivers.  This may take a long time.
Could not find device for /boot: Not found or not a block device.

Any help would be greatly appreciated.

Thanks,
Ken

---

### Post by merlinus on 2007-05-20
Can you run sudo fdisk -l from a terminal after booting with the live cd?  This should offer better information about your partitions, and maybe help with where grub needs to be installed.

Good luck!

-merlin

---

