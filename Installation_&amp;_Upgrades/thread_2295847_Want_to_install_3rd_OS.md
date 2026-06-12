---
title: "Want to install 3rd OS"
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by Olivares on 2015-09-21
I have a dual-boot desktop PC with Ubuntu 15.04 and windows 8.1. Can someone help with the following queries:

 1. The fdisk command lists the following on my desktop PC:
 /dev/sda1    350 Mb    /HPFS/NTFS/exFAT
 /dev/sda2    449.9 Gb    /HPFS/NTFS/exFAT
 /dev/sda3    481.3 Gb    Extended
 /dev/sda5    474.4 Gb    Linux
 /dev/sda6    6.9 Gb        Linux swap / Solaris
 
 
 My GRUB2 menu lists the following:
 Ubuntu
 Advanced options for Ubuntu
 Memory test (memtest86+)
 Memory test (memtest86+ serial console 115200)
 Windows 8 (loader)    (on /dev/sdb1)
 Windows 8 (loader)    (on /dev/sdb2)
 
 
 Why is Windows 8 listed twice in the GRUB2 menu, and why do they appear as 'sdb' rather than 'sda'? The reading I have done indicates sda & sdb refer to different hard drives, but I have only got one hard drive, surely?

 
 
 2. I want to install Windows 98 as well on my PC, to run an application which only works on older versions of Windows. I have read articles 'MultiOSBoot' and 'HowToResizeWindowsPartitions' on help.ubuntu.com. The first of these specifies using version 1 of GRUB whereas I think I have version 2. The second one is applicable where Windows occupies the whole hard drive and it has to be shrunk to accommodate Ubuntu. Neither of them seem to tell me what to do. Can someone either set out the procedure, or refer me to articles which do.

---

### Post by oldfred on 2015-09-21
Your Windows has to be on a primary partition. You do have one primary left, but should make sure it is before the extended partition to avoid issues.

Have you run this:
sudo update-grub

Sometimes flash drive is promoted to sda, and then installer sees hard drive as sdb.
You probably have boot files in both sda1 & sda2, so grub2's os-prober finds both. Grub looks for boot files. Windows uses boot flag to know which partition to boot, grub does not use boot flag.

You will have to shrink Ubuntu, move it right inside extended and then shrink extended so you have unallocated outside of extended so you can make sda4 as a primary.

I have forgotten? Does Windows 98 use FAT32?

While not Windows 98, BIOS with MBR partitioning still is the same.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Olivares on 2015-09-29
Thank you for the advice, its been most helpful. I have got as far as shrinking sda5, and I have done this using the Live CD. The next step is shrinking the extended partition. The partition has to be unmounted in order to do this. Going to File Manager, it lists '483 GB Volume' and '436 GB Volume'. The former is apparently Windows, and the latter is Linux. I right click and select 'unmount.' Then go back to GParted, and the extended partition still shows as mounted and the resize / move option is greyed out. How do I proceed?

---

### Post by yancek on 2015-09-29
You need to unmount the logical partitions first, sda5 and turn swap off before trying to modify the Extended partition.

Have you read anything about what will happen when you install windows 98 on a computer with windows 8.  Hardware compatibility,  Windows bootloaders are backward compatible but I can't see any way windows 98 will boot windows 8 and most windows systems will install their own bootloader.  Also the UEFI thing might be a problem.  You might be better off trying to run it in virtualbox.  The two windows 8 entries are probably the system and the recovery partition.

---

### Post by oldfred on 2015-09-29
+1 on unmounting swap or swap off

@yancek
If drive is MBR(msdos) or has an extended partition, Windows must be installed in BIOS boot mode. 
Windows with UEFI must be on a gpt partitioned drive. 
Windows 8 still installs in BIOS mode, its just all pre-installed Windows 8 systems by a vendor are UEFI.


What I do not know is if Windows fast start will hibernate all partitions( I think it does) and then OP will have issues with any other Windows install.

---

### Post by Olivares on 2015-10-06
Comments by Yancek about installation of Windows 98 alongside Windows 8.1 had me worried, so I thought I would try VirtualBox - which I hadn't heard of before. I am stuck at the point of installing the display driver. The recommended one is apparently Scitech Display Doctor version 7 beta. It is supposed to identify monitor and graphics adapter before installing their driver. Although it lists dozens of Samsung monitors, it doesn't list mine (19" S20C300). Advice on Youtube video said to increase video memory to 32 Mb. Monitor and adapter still don't show up. If I go ahead and install Scitech driver, I get Windows protection error message and Windows won't boot up. Do you have any suggestions?

---

