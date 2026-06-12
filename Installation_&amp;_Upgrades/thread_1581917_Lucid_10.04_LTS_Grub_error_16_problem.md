---
title: "Lucid 10.04 LTS Grub error 16 problem"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by Odipides on 2010-09-25
I've checked a lot of sources to see if anything has been written about this issue but the closest I've come is where someone had a faulty SATA cable and I'm pretty certain that's not the problem here.

Another line of investigation suggested that this is a bug whereby Grub doesn't honour the BIOS drive order and screws up as a result.

Although this is (allegedly) 10.04 LTS, the system seems to be running Grub not Grub 2, grub --version displays "grub (GNU GRUB 0.97)" which I find a bit odd. It also tells me that I can't upgrade to grub2 because there's some package breakage.

Output of attempt to upgrade Grub =========================== 
sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  grub-pc: Depends: grub-common (= 1.98-1ubuntu5) but 1.98-1ubuntu6 is to be installed
E: Broken packages
===========================================================


Symptoms:
1) Clean install of 10.04 - No problems encountered
2) Shutdown machine and power off
3) Added 2 new SATA drives after the install (to copy the contents onto the new disk)
4) Start machine
5) Gave error 'out of disk' and dropped into the grub rescue> mode (which didn't understand ANY of the normal grub commands)
6) Booted with Live CD, ran fsck -p -t ext4 /dev/sda1 which picked up a load of inode errors (and fixed them)
7) Rebooted. 
8) Machine came up perfectly

Then I powered it down again to put the case back on properly

9) Power on
10) BIOS starts normally, lists all the drives (BIOS output)
11) Then gives: "Grub loading, please wait..." followed by "error 16" at which point the PC hangs
12) Ctrl-Alt-Del to restart
13) Machine boots perfectly again

Steps 9 to 13 are 100% reproducible

I don't think it's a cable problem because (surely) it wouldn't ever work then or at least not reliably and I am currently entering this missive on the machine in question. As soon as it's rebooted, it works perfectly.

I've tried all sorts of things (changing the drive order in the BIOS, moving the SATA connectors around, re-installing Grub


Output of sudo fdisk -l ====================================
~$ sudo fdisk -l
[sudo] password for paul: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015d51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120284   966175744   83  Linux
/dev/sda2          120284      121602    10584065    5  Extended
/dev/sda5          120284      121602    10584064   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x367e367d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121600   976751968+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a706adf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x113b113a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17a0179f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30400   244187968+   7  HPFS/NTFS

===============================================

Any ideas?

---

