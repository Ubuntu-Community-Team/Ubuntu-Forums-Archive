---
title: "The ext4 file system creation fails on single partition (no raid)"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by relaxnjaxon on 2010-05-14
I can't seem to get past step 6 of he installation of Ubuntu 10.04.
I get the error: The ext4 file system creation failed... on single partition (no raid).
I chose ' / ' as the mount point, and have tried with and without a swap drive.    I'm installing on a Sony VAIO VGN-NS160D, and the HDD was previously formatted to NTFS.  Am I doing something wrong?  There's no other OS so I don't see any way of getting a command line to try a sudo fdisk...Please, somebody, help!

---

### Post by srs5694 on 2010-05-15
I don't recall precisely what the Ubuntu installer does, but you can usually switch from a GUI installer to a text-mode shell by using the Ctrl+Alt+F1, Ctrl+Alt+F2, Ctrl+Alt+F3, or similar keystroke. Alt+F6 or Alt+F7 usually switches back to the GUI installer.

You could also try using [PartedMagic,](http://partedmagic.com) [System Rescue CD,](http://www.sysresccd.org) or a similar tool to do your partitioning. Once you've done this and rebooted the Ubuntu installer, select the "manual" or "advanced" partitioning option (I don't recall precisely what it's called) to assign mount points to your partitions.

As a side note, if you don't plan to install Windows, I recommend you use the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) rather than the older (and default) [Master Boot Record (MBR).](http://en.wikipedia.org/wiki/Master_boot_record) GPT has a number of minor advantages over MBR, such as checksums to detect partition table data corruption, a backup copy of the partition table being automatically stored on the disk, elimination of the trouble-prone primary/extended/logical partition distinction, and names for partitions in the partition table. GPT also handles disks bigger than 2TiB, which isn't yet important for most people but will make a transition to GPT necessary for most people before too long. If you go with GPT, be sure you create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) for use by GRUB.

---

