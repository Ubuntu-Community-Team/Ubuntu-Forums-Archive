---
title: "Installing Ubuntu 14.04 64 bit UEFI with Windows 7"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2014-05-22
Hi,

I have a system with installed window 7 64 bit. Now I want to install Ubuntu 14.04 64 bit. I can only install the UEFI version of Ubuntu since the standard mode does not boot from live DVD. I have made a new UEFI partition at beginning of my first hard drive /dev/sda1 and I have substituted the windows hidden boot partition. My configuration is this:
```

sudo fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb25eb25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      614399      306176    b  W95 FAT32
/dev/sda2          614400   145739775    72562688    7  HPFS/NTFS/exFAT
/dev/sda3       295647232   976773167   340562968    7  HPFS/NTFS/exFAT
/dev/sda4       145739776   295647231    74953728   83  Linux

```
The first partition is UEFI with boot flag. The second is windows 7 while the third is Ubuntu. The last is another NTFS partition. The problem is that the system does not find grub and is broken. I have also tried to use boot-repair [http://paste.ubuntu.com/7502798/](http://paste.ubuntu.com/7502798/) without success.
Any suggestions?
Thank you

---

### Post by oldfred on 2014-05-22
Windows only boots in UEFI mode from gpt drives.
Ubuntu can boot in UEFI mode or CSM/BIOS from gpt partitioned drives.
Both Ubuntu & Windows only boot in BIOS mode from MBR(msdos) partitioned drives.

Your drives are both MBR. So you do not need an efi partition as you are not booting in UEFI mode. Although I leave space on new drives for an efi partition in case later I move drive to a new UEFI system.

You need to make sure system has UEFI turned off and/or CSM/BIOS boot mode turned on. And system set to boot from drive that is sda, the 500GB drive.

It looks like you had UEFI boot files in the efi partition, Boot-Repair has converted install to BIOS boot mode.

I would also install the nVidia drivers from system settings, drivers tab.

With nVidia you will need nomodeset to boot until you install the proprietary driver. With 14.04 default low level graphics with nomodeset made screen very large and I had a bit of an issue getting into system settings and then the Software and drivers tab. They were off the bottom of the screen.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

