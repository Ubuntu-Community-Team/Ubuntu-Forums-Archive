---
title: "ubuntu 14.04 /boot partition deleted maybe after installing centos"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by shubh9835 on 2014-09-24
hi! i had ubuntu 14.04 up and running on my laptop smoothly. for some reasons i wanted to setup a dual boot with centos. actually i had fedora in one of the partitions of which i thought to format and install centos. i think i made some mistake while installing centos which resulted me to end up with a scary grub rescue screen. so i tried to do repair the boot with boot repair software booting up a live usb of ubuntu which prompted me to uninstall grub. i could uninstall successfully but it could never reinstallit. so i thought of setting up ubuntu again on the partion with centos installed. i thought i'd be presented with a dual boot with my primary ubuntu but there was no dual boot.

i have my / directory of the primary ubuntu partition intact. 
any help regarding fiing my primary ubuntu partition?
thanx



output for sudo fdisk -l

sudo fdisk -l
> 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd9fa2484

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      718847      358400   83  Linux
/dev/sda2   *      718848   204802047   102041600   83  Linux
/dev/sda3       204802048   716802047   256000000    7  HPFS/NTFS/exFAT
/dev/sda4       716804094  1953523711   618359809    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       716804096  1881358335   582277120    7  HPFS/NTFS/exFAT
/dev/sda6      1881360384  1882384383      512000   83  Linux
/dev/sda7      1882386432  1953523711    35568640   8e  Linux LVM

Disk /dev/sdb: 7773 MB, 7773585408 bytes
255 heads, 63 sectors/track, 945 cylinders, total 15182784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          90    15182783     7591347    c  W95 FAT32 (LBA)

Disk /dev/mapper/fedora-root: 28.9 GB, 28886171648 bytes
255 heads, 63 sectors/track, 3511 cylinders, total 56418304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-root doesn't contain a valid partition table

Disk /dev/mapper/fedora-swap: 7532 MB, 7532969984 bytes
255 heads, 63 sectors/track, 915 cylinders, total 14712832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/fedora-swap doesn't contain a valid partition table


/dev/sda2 being my root directory of primary ubuntu installation

---

### Post by oldfred on 2014-09-24
Best not to let any of the installs use LVM. I think your Centos install defaults to that. LVM is ok if you have the entire drive and then later want to move partitions around a lot. But it adds a level of complication.

You cannot share /boot partitions. The LVM will have to have one, but do not use /boot partitions with any other install. You may be able to share a data partition if all installs use UID 1000 for first or admin user.

Best to see details. With multiple installs or multiple drives always good idea to run this report to know what is where. I also run the bootinfoscript which is just a script and actually is the first part of Boot-Repair's summary report.
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by shubh9835 on 2014-09-24
> **oldfred said:**
> Best not to let any of the installs use LVM. I think your Centos install defaults to that. LVM is ok if you have the entire drive and then later want to move partitions around a lot. But it adds a level of complication.

You cannot share /boot partitions. The LVM will have to have one, but do not use /boot partitions with any other install. You may be able to share a data partition if all installs use UID 1000 for first or admin user.

Best to see details. With multiple installs or multiple drives always good idea to run this report to know what is where. I also run the bootinfoscript which is just a script and actually is the first part of Boot-Repair's summary report.
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

so i tried repairing with the boot-repair tool like a million times . i got a error everytime
here's the bootinfo summary [http://paste.ubuntu.com/8419193/](http://paste.ubuntu.com/8419193/) . i would have reinstalled ubuntu but i have a lot of data which i don't want to loose.
btw the 4th line from bottom in the above report which says "Found Ubuntu 14.04 LTS (14.04) on /dev/mapper/fedora-root" thats not the ubuntu i want to be recovered. i installed it over the centos installation. 
the primary installation exists on dev/sda2  . while installing ubuntu i configured only the "/ " and "/boot " partitions, i had made swap area before for fedora which i was using.
/dev/sda2 being the "/"

---

### Post by shubh9835 on 2014-09-24
and now i get the error minimal bash-like shell .press tab....

---

### Post by oldfred on 2014-09-24
I am not seeing any kernels in sda1 or sda2?

Boot-Repair has an advanced uninstall of grub and full reinstall. I think that also updates to the latest kernel, or if not you need to include that as part of the reinstall of grub.

Boot-Repair finds various misc errors and reports those. Typically you will see it reinstalled grub with error code 0 and that is that it reinstalled grub correctly. 
You do show a grub install to the partition boot sector of sda2. That will never be used, but do not install grub to partitions.
The os-prober looks for other installs so that is normal if it finds other installs and adds those to grub menu.

If Boot-Repair does not work then we can do the full chroot into your install to update it by totally uninstalling grub & reinstalling grub and new kernel.

---

