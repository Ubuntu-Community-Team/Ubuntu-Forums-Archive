---
title: "Installing to two identical drives"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Dustyco.net on 2010-02-25
I'm trying to install Kubuntu 9.10 64-bit Alternate to a pair of WD6401AALS drives on my Asus M4A785-M.  My goal is to have both drives configured as follows:

sda:
  64 GB - NTFS - Windows
  ~576 GB - ext3 - Windows data, linux /home
sdb:
  32 GB - ext4 - linux /
  8 GB - swap
  ~600 GB - NTFS - Windows program files

My motherboard has 3 SATA port modes: IDE, RAID, and AHCI

I've tried AHCI mode but at the end of the installation process, grub fails
With IDE mode, the installation completes and I boot but a few seconds into the loading splash the screen goes black and I hit a key to get this console feedback:
```

mount: mounting /dev/disk/by-uuid/183c6674-61c0-4372-b78d-026b94d42f7e on /root failed: Invalid argument
mount: mounting /sys on /root/sys  filed: No such file or directory
mount: mounting /dev on /root/dev filed: No such file or directory
mount: mounting /sys on /root/sys filed: No such file or directory
mount: mounting /proc on /root/proc filed: No such file or directory
Target filesystem  doesn't have /sbin/init
No init found. Try passing init= bootarg.


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

```When I boot to a live cd and check /dev, all I get is sda and sdb, no partitions

On a side note, I want to configure a~576 GB /home and windows data partition so that both OS's have regular read/write access.  I was planning on trying ext3 and ext2fsd to mount it in windows but if anyone else has a better plan, I'm all ears.

[edit]
I decided to see what GParted has to say on a live cd and it came up with some strange reults:
There are 3 devices:
/dev/mapper/isw_bfefijbja_WDBLK640X2 (1.16 TiB)
/dev/sda (596.17 GiB)
/dev/sdb (596.17 GiB)

I was running Windows 7 RC on a RAID 0 array configured in the proprietary raid setup menu during boot (until the RC license started threatening to expire in a week).  Before attempting to install linux, I disabled the array, setting the drives back to individuals (because I couldn't figure out how get ubuntu to see the device - drivers?).  Anyway, I set the SATA mode in the bios to AHCI then IDE as stated above but I also tried the software RAID option in the ubuntu setup partitioner before settling on separating the drives.  This is starting to make me think the drives are still linked somehow some way and it's confusing ubuntu.

GParted says it's deleting the /dev/mapper/isw.... device but it just sits there for x minutes without anything happening.

Thanks in advance!

---

### Post by Dustyco.net on 2010-02-26
Anyone?

---

### Post by oldfred on 2010-02-27
The drives has some internal settings that confuse grub/ubuntu:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) remove dmraid

If you are installing on RAID you need to use the Alternate Install CD (image). Read here about the difference:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

