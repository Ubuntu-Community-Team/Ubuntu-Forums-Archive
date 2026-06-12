---
title: "The attempt to mount a file system with type ext4 in SCSI5 (0,1,0), partition #2 (sda"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by soylentgreen2 on 2014-12-26
Hi, Ubuntu forums!
About a day ago, I assembled my PC, new hardware and all. Seeing as Windows costs a  pretty penny, I've decided to install Ubuntu. I created a LiveUSB of  14.04.1 (the ISO was downloaded from the official Ubuntu site, and the  checksum was verified for the AMD 64 version), and plugged it into the  new PC. I get to the installation screen, where it gives me the option  to delete everything and install, or partition the disk myself.  Naturally, I didn't want to mar the process of correctly formatting and  partitioning my disk, so I selected the "delete everything and install  Ubuntu" option, which I ha expected to work just fine, as the drive was newly purchased and completely empty. Seconds later, an alert appeared with the following message: 

  "The attempt to mount a file system with type ext4 in SCSI5 (0,1,0), partition #2 (sda) at / failed"

  I've never actually had to do anything with formatting/partitioning a drive before, and I've been searching for hours for a solution to the problem. Some threads say it could be the integrity of the ISO, but I verified the hash from the website. I personally suspect it could be something to do with my BIOS settings, but I am really unclear about the whole thing.
Any ideas or recommendations would be 100% appreciated. Thanks!

---

### Post by grahammechanical on 2014-12-26
7 years ago I built my own machine and installed Ubuntu on to a blank hard drive, as you are doing, using the Erase disk and install Ubuntu option. I cannot now remember if I needed to create at least one partition with a format (file system - Ext4) but it is worth a try.

The Ubuntu live session has an application called Gparted. That will create a partition for you and format it. Then when you run the installer and tell it to use the entire disk you may succeed.

Regards.

---

### Post by soylentgreen2 on 2014-12-26
> **grahammechanical said:**
> 
The Ubuntu live session has an application called Gparted. That will create a partition for you and format it. Then when you run the installer and tell it to use the entire disk you may succeed.
Regards.

But a partition for what, exactly? Even if I do partition it, when I get to the "delete everything" option, won't it just wipe the partitions and continue to fire errors at me? There's a "something else" option that allows me to make my own partition table, but I'm not sure what to partition, and where to mount.

---

### Post by flaymond on 2014-12-26
You can create partition and reformat using GParted (I recommend you to dual-boot Windows for first time you use, since it can be dangerous if you lose your Windows.) I guess you should try the FAT32 format instead of ext4 for Windows.

---

### Post by oldfred on 2014-12-26
If it is very new hardware, it probably is UEFI, but can be CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Also what motherboard, amount of RAM, CPU and graphics card or chip?

How you boot install media is how it installs.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And with UEFI, you probably have more settings to change. Where with BIOS often could install with few or even no settings changes from defaults.
You may have to turn UEFI fast boot off, turn off secure boot (some may just call it Windows mode), and turn on or off UEFI or CSM boot modes. You may still be able to boot flash drive in both modes.

Most know & understand BIOS with MBR partitions, but that is now 35 or 40 years old with many kluges to keep it working.


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by MAFoElffen on 2014-12-27
I think you guys are overlooking something...

To the OP-- With the LiveCD/install USB, Go into the manual partitioner and see what disks it see's. If I mount a USB to a Linux Box. or if I boot from a USB drive, that USB will show in Linux as /dev/sdx... Since it booted from the USB, and that device is the first drive that Linux sees, that will show up as /dev/sda. (Different than booting from CD/DVD) The partitioner will also fail on trying to partition a drive it is mounted to... It would have indicated that the USB filesystem (SELinux Live image, would have been ext4.

So what might have happened is that it mistakenly was trying to partition the USB drive, instead of the new internal drive. Restart the partitioner and use manual to look for your new drive, which your new drive should NOT have any file system on it yet.

You could certainly use anything as a partioner, meaning the install's partitioner, GParted, fdisk, gdisk or parted, but all the tools are on that LiveCD. All those will edit or add a partition table. Another way to do that  is to "try" and boot into the System LiveImage, then install. That way you have access to allot of other tools, if needed.

Sidenote- No worries that /dev/sda is a USB during an install (and that sdx will change when you remove that), as we use UUID's for drive, partition, node assignment... to make that more universal. On HDD, insure that the HDD controller see's the physical drive. If onboard controller, the BIOS. If HBA, the HBA's BIOS. If not, then there are other things to do first.

---

### Post by ubfan1 on 2014-12-27
I think Grahammechanical's point is to get a partition table onto the disk, then try your install using everything.  The lack of any partition table may be causing the problem.  Before you do that, try reading some recommendations on what partition setups are recommended -- there are many.  The basic idea is to allow updates without affecting your own data.  A separate partition for your own stuff (big), a 20-30 G root (ideally two of them so you can update one and continue running the other), swap, and maybe /boot up front if your disk is so big the firmware cannot boot a file off the end of it.

---

