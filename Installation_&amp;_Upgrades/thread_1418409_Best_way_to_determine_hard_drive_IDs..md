---
title: "Best way to determine hard drive IDs."
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2010-02-28
I have Ubuntu 9.10 & Ubuntu 8.10 & 74Gb NTFS all on the same HDD. On a different HDD is WinXP Home. I thought it's time to take a look at Ubuntu 10.04 & want to install it over 8.10 but don't want to mess up. Is there a simple way to determine hard drives using the terminal? I know Ubuntu 8.10 is on 145Gb.
Thanks

---

### Post by darkod on 2010-02-28
I'm not sure I understood right, bit if you run in terminal

sudo fdisk -l

it will show all disks and the partitions on them. Also their names which can be used to tell them apart (plus the size). Note that the size is usually shown in a number of blocks, one block being 512Bytes, not in GB, MB, etc.

---

### Post by GARoss on 2010-02-28
Originally, the drive was NTFS then partitioned for Ubuntu. Ubuntu 8.10 is 145Gb & was installed before 9.10 which is 75Gb. I want to install Ubuntu 10.04 where 8.10 is now. Would that be sda3 Linux & sda7 Linux Swap / Solaris? I say that because of the proportion of ext4 & Swap.


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9067    72830646    7  HPFS/NTFS
/dev/sda2            9068       36483   220219020    5  Extended
**/dev/sda3           18134       35740   141428196   83  Linux**
/dev/sda5            9068       17758    69810394+  83  Linux
/dev/sda6           17759       18133     3012156   82  Linux swap / Solaris
**/dev/sda7           35741       36483     5968116   82  Linux swap / Solaris**

---

### Post by darkod on 2010-02-28
Yes, according to the size that would be /dev/sda3.

Also, a reminder that you don't need two swap partitions. Linux OSs, even different distros, can use same swap partition because you only have one distro booted at the same time. No need to waste space for two swap partitions.

To double check if /dev/sda3 is 8.10, boot 8.10 and run:

df -h

That will show the mounted partition and free/used space, so it should say like

/dev/sda3 xxxxxxxx / <- that will be your 8.10 root because you booted 8.10

---

