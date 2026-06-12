---
title: "Boot Repair failed, msftres partition &quot;unknown filesystem&quot;."
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by alkh3myst on 2013-04-27
I have a Toshiba C855-S5347 laptop, and I installed 64-bit Ubuntu 13.04 beside Windows 8. The system won't boot into Ubuntu. Boot-Repair failed. I took a look at the partitions with GParted and /dev/sda3, flagged as a msftres partition, came up with a warning and the notation "unknown filesystem". My efi partition is /dev/sda2, /dev/sda1 is a Toshiba recovery partition. Here is my bootinfo summary URL:

[http://paste.ubuntu.com/5607572](http://paste.ubuntu.com/5607572)

Taking a look at the link, I see that GRUB is installed into /dev/sda7, where my root directory is installed. Everybody says don't modify boot-repair settings without expert guidance, so I await help from one of you good folks.

---

### Post by dino99 on 2013-04-27
[http://gparted-forum.surf4.info/viewtopic.php?id=16614](http://gparted-forum.surf4.info/viewtopic.php?id=16614)

---

### Post by oldfred on 2013-04-27
Locked-ESP detected.

Your grub never got installed to the efi partition sda2.
      
 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

The only real work around seems to be to make a full backup of your efi partition, which is a good idea anyway. 
Delete efi partition with gparted. Then recreate a valid efi partition with gparted, format as FAT32, right click flag as boot (which makes it efi), and restore Windows efi files from backup and then grub should be able to install its boot files into an ubuntu folder in the efi partition.

Do not delete any partitions. Several partitions may not be seen from gparted or other tools as they are unformulated or encrypted. If you encrypt /home then swap also does not show. If you boot in BIOS mode a bios_grub partition does not show.

       Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

            Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

