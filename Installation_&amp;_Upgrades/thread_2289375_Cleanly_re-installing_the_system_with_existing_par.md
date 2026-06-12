---
title: "Cleanly re-installing the system with existing partition?"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by raen on 2015-08-03
When I first installed Ubuntu, I set it up so that the system was on one partition and everything else was on another partition. I was told that would safeguard my data in the event of a clean re-install. But I've never worked with partitions before, so I don't know how to clean re-install my system without affecting my data. I'll be going from 12.04 LTS with way too many DEs to the current version. Can anyone help me out?

Thanks,
raen

---

### Post by yancek on 2015-08-03
Since you have only the one operating system (Ubuntu) and another data partition, you would select to install the new Ubuntu to the same partition on which the previous one was installed.  Do you have a separat /home partiton or is it just a data partition?  If it is a /home partition and you are asked during the install, make sure you do NOT select to format that partition.  You might post the output of the command:  sudo fdisk -l(Lower Case Letter L in the command) or and image from gparted showing partitions/drives.

---

### Post by raen on 2015-08-03
```
$ sudo fdisk -l
[sudo] password for me: 


Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d3d6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390627047   195312500   83  Linux
/dev/sda2       390627328  2920509439  1264941056   83  Linux
/dev/sda3      2920511486  2930276351     4882433    5  Extended
/dev/sda5      2920511488  2930276351     4882432   82  Linux swap / Solaris


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8325555


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   629147647   314470400    7  HPFS/NTFS/exFAT
/dev/sdb3       629147648  2930274303  1150563328    7  HPFS/NTFS/exFAT


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x58227d0d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001    7  HPFS/NTFS/exFAT

```

That may or may not also be showing my Windows installation on another hard disc, but I will be physically disconnecting the Windows drive when I re-install Ubuntu.

---

### Post by oldfred on 2015-08-03
Post this also:
cat /etc/fstab

If sda2 is /home then use Something Else and choose sda1 (change) as / (root) and format it so it erases all your old system. And choose sda2 as /home, but DO NOT tick the format button.

---

### Post by raen on 2015-08-03
```
$ cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=87718c8d-0144-4611-9949-fb5d2f533846 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=c6bdbff2-91ec-4527-bf02-b9364ce83d88 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=ee6d5fd7-0434-4e91-b283-eeb8becfed07 none            swap    sw              0       0



```

My Windows disc is similarly partitioned, if that helps with interpreting any of this.

Thanks,
raen

---

### Post by yancek on 2015-08-03
How your windows disk is partition should not be relevant for installing a newer version of Ubuntu if the windows disk won't be connected.  sda1 is the filesystem partition to which you should install Ubuntu and sda2 is the /home partition with your personal data so follow the suggestion by oldfred.  You never mention which version of windows you have and that could make a difference since if you have 8 or newer you may have UEFI.

---

### Post by raen on 2015-08-03
> **yancek said:**
> How your windows disk is partition should not be relevant for installing a newer version of Ubuntu if the windows disk won't be connected.  sda1 is the filesystem partition to which you should install Ubuntu and sda2 is the /home partition with your personal data so follow the suggestion by oldfred.  You never mention which version of windows you have and that could make a difference since if you have 8 or newer you may have UEFI.

I mentioned that my Windows was partitioned in case the information I posted earlier showed my Windows side as well. I couldn't really tell. Anyhow, I currently have 7 (64-bit) but I'll be updating to 10 once I can get things fixed up on that side, as well as possibly installing XP (32-bit) alongside it for legacy software. (Will it matter which system I upgrade first? I really don't know how to handle GRUB if anything goes wonky.)

Thanks,
raen

---

### Post by oldfred on 2015-08-03
As long as grub is on Ubuntu drive and Windows boot loader on Windows drive, you should not have issues.
But either disconnect Ubuntu drive or make sure BIOS is set to boot from Windows drive when updating Windows. There have been cases where Ubuntu drive was set as boot in BIOS and Windows just installed a new 100MB boot partition at beginning of Ubuntu drive, erasing Ubuntu.

---

### Post by raen on 2015-08-03
I definitely plan to physically disconnect drive X when re-installing on drive Y.

---

### Post by raen on 2015-08-03
> **oldfred said:**
> Post this also:
cat /etc/fstab

If sda2 is /home then use Something Else and choose sda1 (change) as / (root) and format it so it erases all your old system. And choose sda2 as /home, but DO NOT tick the format button.

To be clear, when I re-install my system, I should make sure things look like the screenshot you posted, except for un-checking the format button?

---

### Post by oldfred on 2015-08-03
I do not have a /home, so do not have a screen shot of that. 
And yes, you make sure the /home partition does NOT have the check mark. Otherwise it will erase your data.
If you have made a lot of system settings manually, you may want to back up /etc. That would be if you manually had to change Internet configuration or edited grub. As those system settings in /etc will be overwritten.

Always best to have good backups, which you really should have anyway. Hard drives do fail. But often the biggest problem is us. Sometimes some of us who think we know a little bit will rush thru things and make errors, so everyone should have backups.

---

### Post by raen on 2015-08-03
I've definitely backed up my data, but thanks for suggesting I also back up /etc.

Thanks!

---

### Post by raen on 2015-08-03
One more question: Since I'm multi-booting, does it matter if I re-install Windows first or Ubuntu first?

---

### Post by oldfred on 2015-08-03
Slightly easier to install Windows first. 
Windows always takes over MBR, and if you then want grub you have to reinstall it. 

But you can easily reinstall grub, so not a big issue.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by raen on 2015-08-03
Then I'll do the Windows side first. Thank you. :)

---

