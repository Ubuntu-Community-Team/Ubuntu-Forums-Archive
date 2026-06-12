---
title: "Installation on sda2 failed with error message"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by OlivierJJ on 2008-08-05
Hi all, one more new user ...:lolflag:
I would like to feel more confident will Linux. A friend of mine
told me that the best one is Ubuntu...
So I'm trying to install it on a system that i've built and
of course i have troubles.
My system is based on a 2.4 Prescott proc, chipset Intel 845 and
a 160 Gb SATA disk.
First I tried to install directly Ubuntu on my disk, using CD ROM
but my disk was never seen by the system.
So looking at the forums, I tried to install first XP pro (that's ok).
I made two partitions on my disk, one for Windows, one for Ubuntu.
When I boot with Ubuntu CD, without install, i can see my two partitions, that's ok now.
When i want to install it, the guided proposes me to install
system on sda2, where i can see that i have 73 Gb free.
That's ok for me and i press continue but i get a message
telling that the size is too small .........
What's wrong ? Where do I mistake ?
Thanks for your help, hoping that my english is enough fluent to 
explain my issue.

---

### Post by prshah on 2008-08-05
> **OlivierJJ said:**
> 
I made two partitions on my disk, one for Windows, one for Ubuntu.
When I boot with Ubuntu CD, without install, i can see my two partitions, 

What filesystem ("Id") is your sda2? Open a terminal, (Applications-Accessories-Terminal) from the live CD and use the command ```
sudo fdisk -l
``` the "Id" should be Linux. Example:```
laptop:~$ sudo fdisk -l
[sudo] password: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62bf62bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2932    23551258+   c  W95 FAT32 (LBA)
/dev/sda2            2933        3008      610470   82  Linux swap / Solaris
/dev/sda3            3009        3964     7679070   83  Linux
/dev/sda4            3965        4864     7229250   83  Linux

```

If it's not, post back (with output) for more instructions. Actually, you might as well post the output anyway.

Also, you will need one more partition (a small one) for swap. Ideally, this should be 1.1 times your RAM; if your RAM is 1Gb, swap should be 1.1Gb- this is required for hibernate support.

---

### Post by Kevbert on 2008-08-05
Go for a Manual install rather than guided.  Using the manual install delete sda2.  Then set up a swap file to 2 x your memory maximum.  Set a second partition to use the rest of the disk (which was sda2) format to be ext3, with a mount point of /
The error was that Ubuntu is trying to use the hard disk space at the end of the disk (after sda2) which can be up to 8Mb so it reported this a being too small.

---

