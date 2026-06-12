---
title: "Partition upon installing"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Jinxzs on 2010-08-09
hi guys please help me i am very newbie in ubuntu.

heres my problem

i want to partition the only hardrive i have just like usually how they do in windows.
i want to separate the [COLOR=Red]system file[/COLOR] and my [COLOR=Red]file/documents.[/COLOR]

[COLOR=Red]how to do it?[/COLOR]

i did make partition of [COLOR=Red]/[/COLOR] and [COLOR=Red]/home[/COLOR] and[COLOR=Red] swap[/COLOR].

but it shows only one partition after the installation.

please tell me how to do it
i read the manual but i really dont get it T.T
please spare a time with this, im really love to switch in ubuntu.


--
im so sorry if my explanation is so not clear. :)

---

### Post by lechien73 on 2010-08-09
Please could you open a terminal window, run the following command, and then post the output here?

```
sudo fdisk -l

```
That will help us to see how your hard disk is currently partitioned, and then we can help you further.

---

### Post by Jinxzs on 2010-08-09
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2719924a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       19456   115322602+   f  W95 Ext'd (LBA)
/dev/sda5            5100       19456   115322571    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004037b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1095     8787968   82  Linux swap / Solaris
/dev/sdb2            1095       19458   147500033    5  Extended
/dev/sdb5            1095       10821    78124032   83  Linux
/dev/sdb6           10821       19458    69374976   83  Linux

---

### Post by Ginsu543 on 2010-08-09
Please help me understand exactly what you are trying to do. According to your output, it appears you have two disks, one with two NTFS partitions (one primary, the other extended) and another with three (one primary, two extended). I'm assuming that your first hard drive is used for your Windows C: and D: drives. You are trying to partition the second drive for Ubuntu but so it mirrors the way your Windows system is organized? Does this sound right?

Assuming the above is true, it looks like you set aside ~10 GB for your swap partition, ~80 GB for your / partition, and ~70 GB for your /home partition. That is way too much space for swap and / partitions and not enough for your /home. If I were you, I would reinstall Ubuntu using the following partition scheme:

1) 25 GB for / partition
2) 130 GB for /home partition
3) 5 GB for swap partition

I would also make each of those primary partitions (each time you allocate space, make sure the "primary" option is checked). That would make /dev/sdb1 your / partition, /dev/sdb2 your /home partition, and /dev/sdb3 your swap partition.

You don't need a huge swap partition. In fact, if you have more than 2 or 3 GB of RAM, you may not need a swap partition at all. However, if you want to be able to hibernate or for just in case, 5 GB is PLENTY (you might even cut it down to 2 or 3 GB and put it towards your / or /home partition). If you don't have a lot of ram (1 GB or less) though, it's a good idea to have a swap partition that is 2 x the size of your ram.

Your / partition is where most of your system/program files will be installed. So if you are planning to install a lot of programs, you need a bigger / partition. I recommended 25 GB because in my experience that has been PLENTY. Just to give you an idea, I currently have 1634 packages installed and I'm only using 5 GB of my 25 GB. If you think 25 GB is too much, you can always cut it down to 20 GB and put the remainder into /home. You could even get by with 10 GB.

Typically, you want your /home file to be as large as possible because that is where all your configuration files and data files (such as music, pictures, movies, and documents) are stored.

Partition schemes in Ubuntu, like most things in Linux, is based on personal preference. I've given you some recommendations based on how I use my computer, but my recommendations may not be the best for how you use yours. Experiment! Try different partition schemes and find the one that best suits you.

---

