---
title: "Dual boot Lucid LTS server install w/Win XP"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by JKH Designs on 2010-10-29
Hello,

I have a 320gb single hard drive running Win XP with only 35 GB being used by XP.  Before installation I ran defrag on this drive. I installed Lucid 10.04 LTS server LAMP by using the Guided partition LVM option at 25% space allotment.  The Lucid install was successful. I then proceded to install Kubuntu desktop which also was successful on boot up by holding shift the GRUB menu comes up, XP is not showing up in the menu have I lost my Win XP?  Is it possible to find XP and add it as an option to the GRUB menu? 

All help on this will be very much appreciated.

James

---

### Post by mikewhatever on 2010-10-29
Try running **sudo update-grub** from a command line application in Kubuntu (is it Konsole?). That should try and detect all other OSs, and add them to the bootloader's menu. You can check if the XP partition is still there by running the **sudo fdisk -l** command.

---

### Post by JKH Designs on 2010-10-31
Hello mikewhatever,

Thanks for the response.  I tried your suggestions with the update grub it did not find the Win XP OS and here is the results  of the fdisk -l command

> sudo fdsik -l
sudo: fdsik: command not found
> sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aaa53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       38914   312320001    5  Extended
/dev/sda5              32       38914   312320000   8e  Linux LVM

I guess this means that the 25% partition format did not work on the install and it wiped the entire hard drive.  Is that the way you interpret this?  I also tried a Super Grub2 Disk that I read about it did not detect a WinXP OS either.  So I guess I am down to a Kubuntu only system.

Thanks again for your help.

James

---

