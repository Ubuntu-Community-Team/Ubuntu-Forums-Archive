---
title: "Is my partition scheme normal?"
date: 2017-09-05
forum: Installation &amp; Upgrades
---

### Post by cecilieaux on 2017-09-05
Before doing a clean install upgrade, I am checking the partitions installed. Below is what I have.

$ lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sda 8:0 0 931.5G 0 disk
&#9500;&#9472;sda1 8:1 0 1000M 0 part /boot/efi
&#9500;&#9472;sda2 8:2 0 1000M 0 part /boot
&#9500;&#9472;sda3 8:3 0 97.7G 0 part /
&#9500;&#9472;sda4 8:4 0 823.6G 0 part /home
&#9492;&#9472;sda5 8:5 0 8.3G 0 part [SWAP]

SDA1 is formatted as FAT32
SDA2 as ext2

The other two are ext4s

I plan NOT to reformat /home but I am wondering about the first two partitions and whether they MUST be formatted that way. Anyone have any idea?

(Yes, I contacted the guy who built the machine but so far no answer.)

Thanks, all.

Cecilieaux

---

### Post by ajgreeny on 2017-09-05
It is not advised to use a separate /boot partition unless you are using encryption or LVM partitioning, in which case one will be created and is necessary (if using the full default installation method).  For normal unencrypted installation on ext partitions it simply adds another potential problem, particularly if it becomes full and stops further upgrades of kernels used.

Assuming this is a UEFI machine you must have the first /EFI partition (200MB recommended) and it must be fat32 and have the boot flag; / and /home partitions are best, in my opinion, as ext4 as you intend to use.

97.7G is very large for a root partition; I use 20G and it is never filled more than 50%, also 8G for swap may be too much unless you have a real need to hibernate and have no more than 8G ram; most users seem to recommend 2 - 4G swap irrespective of the amount of ram you have as the old idea of having swap of 2x ram is now long out of date and largely ignored.

---

### Post by oldfred on 2017-09-05
You need the FAT32 as the ESP - efi system partition for UEFI booting. New install will overwrite the /EFI/ubuntu folder in the ESP.

Generally you do not need a separate /boot partition, except perhaps with server installs or full drive encryption which uses LVM. It just adds another partition to manage and make sure it is not full. Yours is pretty large so that is not an issue.Make sure it is housecleaned as old kernels will not be in dpkg to allow easy cleanup, so may be better to reformat. Some that have upgrades have multiple versions of old kernels that become difficult to houseclean.

I typically use 25GB for / (root) partition and 2GB for swap, and when doing clean install, use a new /, so I can still boot old one in case of issues or if I forgot something. With 17.04 or later, it does not create a swap partition but uses a swap file. But if swap partition found it will still use it.
I do not use /home but have a /mnt/data, but that is mostly because I have several installs and want the same data in all of them, but not user settings.

Either way you need to have good back ups of /home, list of installed applications, perhaps some settings from /etc or your normal backup.

---

### Post by Dennis N on 2017-09-05
It's normal, but not efficient. If you have just one OS installed, the FAT 32 EFI system partition (1 gB) is way too big. For mine, I use just 80 mB and that accommodates several OSes. The boot partition is not necessary - the only thing you can do with it is fill it up with old kernels.

---

