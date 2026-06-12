---
title: "Install Ubuntu 12.04 on separate HDD with Windows 8 -- no GUI after booting"
date: 2014-01-30
forum: Installation &amp; Upgrades
---

### Post by larrylisky on 2014-01-30
The last two days I have been trying to install Ubuntu 12.04 64-bit on my Toshiba x75-A7290. My system has three drives, two of them are allocated to pre-installed Windows 8, and the third (SSD) is where I want to install Ubuntu. I burnt the ISO on the USB drive and booted from USB, and ran square into the UEFI madness, have to use 'nomodeset' to see the installer on the screen. After installation complete and subsequent reboot (with Ubuntu SSD being the first in boot order), Ubuntu booted to a console (no GUI). I tried a variety of things listed in the forum, lightdm, startx and apt-get nvidia-current, none of them worked. A couple of times I was able to see some errors flashed on the screen related to [drm:drm_pci_init...], so I suspect it might be something related to nVidia driver. 

Has any one successfully booted Ubuntu on a Toshiba x75 with Windows 8 pre-installed? Any pointer would be greatly appreciated.

-larrylisky

---

### Post by fantab on 2014-01-31
Have followed the instructions at: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)?
Search the forum you'll find lots of information.

If you still have issues then start by posting the output of the following commands after booting with Ubuntu Live DVD/USB, "Try Ubuntu without installing", open Terminal [ctrl+alt+T] to run the commands in:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by oldfred on 2014-01-31
There seem to be some Haswell Intel chip configuration issues.

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

This was a Dell, but they mention a common i915 driver issue.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

---

### Post by larrylisky on 2014-02-01
Hi here are the output of parted and fdisk:

==============
output from 'sudo parted -l':

Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  250MB   249MB   fat32                 boot
 2      250MB   4250MB  4000MB  linux-swap(v1)
 3      4250MB  24.2GB  20.0GB  ext4
 5      24.2GB  245GB   221GB   ext4
 4      245GB   250GB   5000MB  fat32




Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs




Model: ATA TOSHIBA THNSNH25 (scsi)
Disk /dev/sdc: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  1075MB  1074MB  ntfs         Basic data partition  hidden, diag
 2      1075MB  1347MB  273MB   fat32        Basic data partition  boot
 3      1347MB  1482MB  134MB   ntfs         Basic data partition  msftres
 4      1482MB  241GB   240GB   ntfs         Basic data partition
 5      241GB   256GB   14.9GB  ntfs         Basic data partition  hidden, diag




Model: Generic USB Flash Disk (scsi)
Disk /dev/sdd: 8087MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8086MB  8085MB  primary  fat32        boot






==== Output from 'sudo fdisk -l' =========

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006727


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   488397167   244198583+  ee  GPT


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4df31ccf


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 256.1 GB, 256060514304 bytes
256 heads, 63 sectors/track, 31009 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT


Disk /dev/sdd: 8086 MB, 8086609920 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    15792127     7895040    b  W95 FAT32

---

### Post by larrylisky on 2014-02-02
I also tried disabling NIC as suggested by ***oldfred***, that didn't help.  I have to include 'nomodeset' in the GRUB boot parameter on the 'linux' line to even see the GUI, otherwise no boot screen.  But after the system completes booting, the screen went blank, leaving me with only a tty console.  I did see the below error message on the screen before the 'tty1' console showed up:

10.295971] [drm:drm_pci_agp_init] *ERROR* Cannot initialize the agpgart module.
10.295994] DRM: Fill_in_dev failed.

My issue is similar to [this ]("http://askubuntu.com/questions/387729/tons-of-problem-fill-in-dev-failed-black-screen")and [this]("http://askubuntu.com/questions/391786/problem-installing-on-toshiba-qosimo-x75"), but the solution proposed in second thread didn't work for me (and apparently didn't work for the person who started that thread).

I also tried Bumblebee, but that didn't seem to help either.  But I do feel it is related to graphics initialization.  In one mode I could get Ubuntu to boot to the "drum beat" sound, where I should have been able to see the login screen.

---

### Post by oldfred on 2014-02-02
Are you actually booting with Intel Chip enabled, not the nVidia? Then you need different boot parameters. 
Can you set which video chip you boot with or is it automatic?

These are common Intel chip boot parameters, but there are others. UEFI setting may also be required.
acpi_osi=Linux acpi_backlight=vendor

Many with the very new Haswell systems have to use at least 13.10. The 12.04.4 will be out shortly and should have most (or more) updates as 13.10. Intel offered up a lot of changes, not just to video but kernel & support software for Haswell that only is in 13.10 or later.
A few found they could only boot with 14.04, but it still is early and should not be your only install as it gets many changes almost daily.

---

