---
title: "While installing Ubuntu 10.04, it does not detect the existing operating systems"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by magrawal on 2012-02-13
Hi

I have Windows XP SP3 (32-bit) and Ubuntu 9.04 (64-bit) installed on the one and only hard disk in my computer which is a 64 bit machine. When i start my computer, Grub bootloader appears with the options as usual.

I wanted to replace Ubuntu 9.04 (64-bit)with Ubuntu 10.04 (64-bit). I decided to do a fresh new installation of Ubuntu 10.04 (64-bit).

Before proceeding with the new installation, I checked out Ubuntu 10.04 with the live CD which booted out fine. I could see and mount my existing filesystems (windows and ubuntu) from Menu --> Places. However, the G-Parted utility did not show the existing partitions and it showed the entire hard disk space as "unallocated".

After beginning the fresh new Ubuntu 10.04 installation, and entering the time zone (India) and keyboard layout (US), I reached the screen where it said **"This computer has no operating systems on it"**
Then, I clicked on manual partition option but the screen did not show any of the existing partitions. At this point, I quit the installation.

Below is the output of  "sudo fdisk -l" :
----------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1044     8385898+   7  HPFS/NTFS
/dev/sda2            1045        2538    12000555   83  Linux
/dev/sda3            2539       19456   135893835    f  W95 Ext'd (LBA)
/dev/sda4            4961       19456   116439088+   7  HPFS/NTFS
/dev/sda5            2539        2787     2000029+  83  Linux
/dev/sda6            2788        2911      995998+  82  Linux swap / Solaris
/dev/sda7            2912        4960    16458561    7  HPFS/NTFS
---------------------------------------------------------------------------------------------

What is the problem ? How can i get Ubuntu 10.04 to see my existing operating systems during the new installation? 
I want to keep my existing Windows XP SP3 partitions intact and replace the existing Ubuntu 9.04 installation with the new Ubuntu 10.04.
Any help sincerely appreciated. Thanks.

---

### Post by efflandt on 2012-02-13
Something is wrong with your partitioning.  Your extended partition sda3 overlaps primary partition sda4.

sda5, sda6, and sda7 are logical partitions in extended partition sda3, but sda4 should not be within sda3.  So the **end** of sda3 should be 4960 instead of 19456.

Personally I would try using fdisk to remove partitions 5, 6, 7 then 4 and 3 and then recreated 3 with same start and 4960 end, and then recreate 4 through 7 exactly like they are now.  Removing or creating partitions does not destroy any data as long as you do not format or write any other data to the drive, so if that does not work, you could always set everything back exactly like it is now.

But I have experience doing that by trial and error when 64-bit WinXP Pro beta totally changed my partition table geometry (heads & cylinders) years ago, so it could not even boot itself (I fixed it with Linux fdisk with only partial numbers from memory). **But I highly suggest that you back up anything that you do not want to lose before attempting to juggle partitions.**

Note that you cannot repartition a drive you are running from, but could do that from install CD (or bootable iso on USB).

---

### Post by magrawal on 2012-02-14
**@efflandt**:

Thanks a lot for your diagnosis. I have a question - How did you know that "sda4" is the "primary" partition ?

Looking at the output of "sudo fdisk -l" that i attached, the "*" sign under the "Boot" column shows up corresponding to partition "sda1". 

I will try doing what you suggest. But, before that, I just wanted to make sure your assumption (on which the entire reasoning is based) is correct.

As far as I understand your solution, it says that :
1. Boot into Ubuntu 10.04 with the live CD
2. Then, run fdisk utility
3. Remove and recreate partitions as you suggested 

Is my understanding correct ? I do not know how to run fdisk utility. I have never run it before. Is it a GUI based utility or command line ? Can you please mention some link where i can read up on how to use fdisk to remove / recreate partitions ?

Thanks for all your help. Really appreciate you helping out.

---

### Post by btindie on 2012-02-14
> Thanks a lot for your diagnosis. I have a question - How did you know that "sda4" is the "primary" partition ?Partitions 1-4 are always primary partitions on a disk with an MSDOS partition table, partitions 5-* are logical.

> Looking at the output of "sudo fdisk -l" that i attached, the "*" sign  under the "Boot" column shows up corresponding to partition "sda1". That signifies to the bootloader which partition it should boot, though GRUB doesn't work that way. It's used by the standard MSDOS MBR. 

> Is my understanding correct ? I do not know how to run fdisk utility. I  have never run it before. Is it a GUI based utility or command line ?  Can you please mention some link where i can read up on how to use fdisk  to remove / recreate partitions ?Yes that's correct. There's lots of places, just use Google. One of the better resources I like is [http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/](http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/)

---

### Post by westie457 on 2012-02-14
Yiu might find it better to use fixparts. Here is a link to more information. [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

