---
title: "New System partitioning"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by tgm4883 on 2007-04-18
I currently have edgy installed on my 160GB sata drive.  It is only partitioned into root and swap.  I haven't ever partitioned into more than that, but would like to start doing this correctly.  How should I set this partitioning up?  I plan on doing a reinstall soon.  Also, how big should my swap be, I have 1 Gb ram.

And, is it possible to just move my home folder onto my fileserver and then move it back after I create a home partition.  I don't see a problem with that, but then again, never done it before.


```
thomas@poseidon:~$ sudo fdisk -l /dev/sda
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
thomas@poseidon:~$ 

```

---

### Post by raja on 2007-04-18
I dont think there is a "correct" way to partition, but apart from swap and root, I have a separate /home and a 100 MB /boot partition.

---

### Post by tgm4883 on 2007-04-18
> **raja said:**
> I dont think there is a "correct" way to partition, but apart from swap and root, I have a separate /home and a 100 MB /boot partition.

Thats what I meant, I always suck when trying to explain my own situation.

I am trying to create different partitions for different things.  I occasionally reinstall my OS and would like my home directory on another partition.  Some of the other partitions im not really aware of.  What is the purpose of a seperate boot partition?

---

### Post by louieb on 2007-04-18
I play a lot. and have an some opinions on this.[LIST]
[*]/boot if you have BIOS issues (GRUB error 18 ) a separate /boot partition is needed and it needs to be near the start of the drive. Otherwise   it is not needed and you have to make sure it has enough room for the next kernel update.
[*]/home Good to have when you system gets so messed up you have to reinstall. I use mine for all those hidden .config files.
[*]/data I've gone to a separate partition for my data files. Good to have when time for reinstall or. distribution upgrades such as going from Dapper to Fiesty. If its not  a configuration file  then it goes here.[/LIST]Yes you can copy the home folder off, build a seperate /home partition, change your /etc/fstab, and copy the data back (see the psychocats link there is a page on how to do that there). 
I don't belive there is a right way to partition. But you can plan your partition to make life easier at repair and upgrade time.

BtW heres my fstab for the T30
```

sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        4864    23711940    5  Extended
/dev/sda5            1913        2805     7172991   83  Linux
/dev/sda6            2806        3888     8699166   83  Linux
/dev/sda7            3889        4781     7172991   83  Linux
/dev/sda8            4782        4864      666666   82  Linux swap / Solaris

```

---

