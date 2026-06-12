---
title: "installed on hdd by mistake"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by skeptical4life on 2014-09-27
Greetings
I installed Ubuntu alongside windows 8 (64) and failed to notice I was partitioning my external hd. How can I correct this and install on C
Thanks
Michael

---

### Post by QIII on 2014-09-27
Hello!

Linux does not use the Windows convention "C:\ drive".  That is what we would call a partition on the drive.  "D:\" is another.  But they are on the same device.

In Linux, we use the term "drive" or "device" to describe the entire device.  There are partitions on the drive, which might be "/dev/sda1" "/dev/sda5", etc.  The entire device is "/dev/sda".

So you need to be aware of the difference in vernacular.

Most likely, you don't want to install Ubuntu on "C:\" -- a partition which you have come to call "Drive C".  That will wipe out Windows.  You may want to install it on the device, but you will want it in another partition -- which you will have to make room for and create.

So...

Do you want to wipe out Windows completely and replace it with Ubuntu, or create a dual boot system where you can use either Windows or Ubuntu as you choose?

---

### Post by skeptical4life on 2014-09-27
Thanks for helping me with the correct venacular. I want to install Ubuntu alongside windows. I just failed to recognize (when I was installing) that I had selected and was partitioning (and therefore installing Ubuntu on) my external hd not my desktop.
Now my computer won't boot without the ext usb hd connected.
Thanks

---

### Post by Sef on 2014-09-27
1) If you copy and paste this command: ```
sudo fdisk -l
``` that will show what your partitions are, then it would be easier to help you. 
2) There should be an option for Ubuntu to partition your main hard drive on the install disk.

---

### Post by skeptical4life on 2014-09-27
Thank you. When I installed Ubuntu my Freeagent external drive was connected. When I sized the partition for installation I didn't realize until it was too late that I partitioning the usb drive not the desktop. So Ubuntu partitioned and installed on the usb drive. The consequence of this is that the computer won't boot into Ubuntu or windows without the usb drive connected.
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ed65c64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   283594751   141796352    7  HPFS/NTFS/exFAT
/dev/sda2       283594752   488392703   102398976    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009877f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   532267726   266133832    7  HPFS/NTFS/exFAT
/dev/sdc2       532269054   625141759    46436353    5  Extended
/dev/sdc5       532269056   616898559    42314752   83  Linux
/dev/sdc6       616900608   625141759     4120576   82  Linux swap / Solaris
michael@michael-Aspire-5738:~$

---

### Post by oldfred on 2014-09-27
You can easily (relatively) fix your booting by installing the grub2 bootloader to your external drive, probably sdb. but could be something else. And then installing a Windows boot loader to sda. Then set external as default. You then can boot Ubuntu or Windows if external plugged in or directly boot Windows if external not plugged in. This all assumes both Windows and Ubuntu are in same UEFI or BIOS boot mode, not one each.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If boot modes are different, you can only change boot from UEFI/BIOS menu not grub menu. And then post link to the summary report that Boot-Repair can run.

---

### Post by yancek on 2014-09-28
A logical explanation for the behavior you are seeing is that you installed Ubuntu to a partition on the external drive but accepted the default for bootloader installation which installed its code to the mbr of the first drive, the one with windows on it.  That would be if you are using MBR.  If the suggestions by oldfred do not work, you could do an online search for bootinfoscript or boot-repair, download and run either and post the output here.

---

