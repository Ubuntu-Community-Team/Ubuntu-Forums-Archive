---
title: "Big Problem..cannot boot windows/cannot find windows partition"
date: 2017-12-23
forum: Installation &amp; Upgrades
---

### Post by mikeymcg on 2017-12-23
Hello everyone. I just installed a partition onto my windows 10 laptop about 5 hours ago. I have been reading tons of threads for help and troubleshooting and I have gotten no where. I cannot boot into windows, I do not get a grub menu that pops up allowing me to select windows or linux...it just boots into linux, I cannot load from my bootable USB (even after i change boot priorities in BIOS) to possibly delete the partition and try again, and when I run sudo fdisk -l i cannot see any NTFS partitions where windows would be. I absolutely did not delete windows as I was extremely careful in doing this and I used the "other" option and created a partition during install.

This is what I receive after I try sudo fdisk -l

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2a348986

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 156250111 156248064 74.5G 83 Linux
/dev/sda2       156252158 468750335 312498178  149G  5 Extended
/dev/sda5       156252160 312500223 156248064 74.5G 82 Linux swap / Solaris
/dev/sda6       312502272 468750335 156248064 74.5G 83 Linux

Partition 2 does not start on physical sector boundary.




Disk /dev/sdb: 117.8 GiB, 126444634112 bytes, 246962176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0005f17c

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *     2048 246962175 246960128 117.8G  c W95 FAT32 (LBA)

Any help would be appreciated. I have a terabyte hard drive..I allocated 240gigs for linux but I have no issue creating another USB to install ubuntu to load up with windows if this is a possibility. I really hope windows has not been destroyed. Thank you everyone.

---

### Post by oldfred on 2017-12-23
Windows would only be in NTFS partitions.
If you have data you might want to try to recover, STOP using system and only use live installer. More use overwrites more data.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

      [/URL]
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
    
Sometimes testdisk's deeper search may show files, if so immediately copy to another drive.
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by mikeymcg on 2017-12-24
Hey Fred. Thanks for the help. I cannot get linux to boot from the USB. I went into my BIOS settings and made boot priority from USB but my computer just loads straight into linux. Any fix for this? Or anyway I can get access to bootinfo while not using live installer? I really do not understand why I cannot load from usb...doesn't make sense...

---

### Post by oldfred on 2017-12-24
What computer & what version of Linux?
       Ubuntu 17.10 "corrupting" BIOS - many LENOVO laptops models Intel SPI & kernel issue Also some Acer
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

If not Asus and 17.04, you may have done something to installer, so it does not then boot. UEFI only boots a good flash drive.

I always have several flash drives, others with repair tools like gparted, parted magic, Knoppix or my older or newer test versions of Ubuntu. I always want something that boots. I now have all those tools on one flash drive, but still have several bootable flash drives.

I live a couple of miles from a Microcenter. And flash drives are behind the counter. And every time I go in the next size up was cheaper than my previous purchase of a smaller one. Or USB3 versions were cheaper than previous purchase of size smaller, and only a $1 more than USB2 version of that size. I stopped at 64GB, but have several 32GB & 64GB flash drives, most now with full installs and backup data.

---

