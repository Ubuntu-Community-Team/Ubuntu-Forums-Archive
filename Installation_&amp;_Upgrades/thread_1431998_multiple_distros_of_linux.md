---
title: "multiple distros of linux"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by rashil on 2010-03-17
I have a couple of questions about linux.  I want to triple boot Ubuntu 9.10, Fedora 12, and windows 7.  I would like to use grub2 as my bootloader so I know I need to install ubuntu last.  Each OS will be going on a seperate drive.  Windows is already installed.  When I install Fedora, is it suggested I pick the option to use entire disk or to set up partitions manually?  Also, where do I tell Fedora to put the bootloader?  In it's / partition or skip the bootloader?  Same question applies to Ubuntu as well.  Will I also have to edit the grub.cfg to add/boot Fedora from Grub2?  Any help would be greatly appreciated.

---

### Post by phillw on 2010-03-17
> **rashil said:**
> I have a couple of questions about linux.  I want to triple boot Ubuntu 9.10, Fedora 12, and windows 7.  I would like to use grub2 as my bootloader so I know I need to install ubuntu last.  Each OS will be going on a seperate drive.  Windows is already installed.  When I install Fedora, is it suggested I pick the option to use entire disk or to set up partitions manually?  Also, where do I tell Fedora to put the bootloader?  In it's / partition or skip the bootloader?  Same question applies to Ubuntu as well.  Will I also have to edit the grub.cfg to add/boot Fedora from Grub2?  Any help would be greatly appreciated.

Hi,

Install Fedora and let it put it's bootloader on the hard drive you're installing it on. When you install Ubuntu as the last OS, it will ask to put its boot-loader on, tell it to do so, but onto the hard disk that is set up as your Primary Hard Disk (i.e. 1st hard-disk that boots), Grub2 will then have a good look round and add the other operating systems to its list of bootable OS's.

The above assumes that the hard disk that is designated as the primary one will always be powered up. All three will need to be powered up for the initial run of Grub2 to go looking for the other OS's.

You could do it differently, using the BIOS to choose operating systems - but that is the most straight forward way.

Regards,

Phill.

---

### Post by oldfred on 2010-03-17
Essentially the same as phillw, but I would make sure each operating system has its boot loader in the MBR of its drive. Each drive then can be booted without any of the other drives. Your windows drive is probably the default boot drive and the boot loaders will normally install over the windows boot loader. You can manually tell where to install grub as part of the install process with the advanced button near the end of the partitioning screen. It is easier to select in BIOS the drive you are installing to as the boot drive and then install, grub will automatically install to that drive's MBR.

With multiple operating systems you need to think about your data. If you want to share data between installs you should create separate data partitions. Any data to share with windows should be in a NTFS partition and linux only data (but not /home) should be in a ext3 or ext4 data partition to make it easy to access and not get reformated on reinstalls.

---

