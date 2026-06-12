---
title: "New Install- Disk Partition and Failed GRUB Install"
date: 2018-07-22
forum: Installation &amp; Upgrades
---

### Post by jay116 on 2018-07-22
This seems simple but I haven't done an install this way before. I originally did a fresh Ubuntu install over a windows install (single boot Ubuntu 18.04) and walked though the installer. After booted up I wanted to create a snapshot so of my root directory so I could make some changes and rollback if needed. I found the installer used 100% of my /root and I had no space left for snapshots. Instead of trying to shrink the file system and then the LV I'm attempting to boot to the installer liveUSB and from there create the partition setup and the LVM, then do the install so I have a LV on the same VG for snapshots of my /root. Please see below for my partition setup. For some reason the GRUB boot loader doesn't like this and I'm not sure why. The first partition is boot then the second is swap, then my FS is on the LV.  I keep getting the below error about GRUB. If this looks ok maybe i did something wrong and need to double check myself. Any suggestions? Thanks.

[ATTACH=CONFIG]280476[/ATTACH][ATTACH=CONFIG]280477[/ATTACH]
here is my setup:

sda1  ---> /boot (ext4) (1GB)

sda2  ---> /swap  (16GB)

sda3--> PV --> VG (sysvg)---> (LV) lvhome  /home (ext4) (1.5TB)
---------------------------------> (LV) lvroot    /           (ext4) (50GB)
---------------------------------> (LV) lvsnap             (ext4) (100G)

---

### Post by oldfred on 2018-07-22
I do not know LVM as that is an advanced Logical Volume type of partitioning that is inside the physical partitions you show.

But with UEFI system and gpt partitioning you need an ESP - efi system partition. It is FAT32 formatted with boot flag if using gparted, or code ef00 if using gdisk.
The defalt LVM installs I have seen have an UEFI ESP, a Ubuntu /boot partition and a large partition that has all the LVM volumes inside it. If BIOS install on gpt, then it has to have a bios_grub partition. Only installs to the now 35 year old BIOS/MBR configuration only have /boot & LVM container as partitions.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Dennis N on 2018-07-22
Did you create an EFI system partition? I don't see one and it's needed for UEFI. I've been installing using LVM on all my installs over the past 2 years. Be aware that you don't need a boot partition unless you are encrypting the disk. You may not need to create a swap partition - Ubuntu will make a swap file for the OS inside your root partition if no swap partition is found. But, if you multiboot with another non-Ubuntu OS, you probably do need one.

Do any disk setup (partitions, physical volume, volume groups, logical volumes) before starting installer. Then use the 'something else' option when you choose installation type to get to the partitioning screen where installer will show you the LVs available at the top. Pick the one to be used for root, select 'change' and in the dialog select file system ext4, format it, and mount at / . You can make the other LV later from within Ubuntu.  Then proceed with install.

---

