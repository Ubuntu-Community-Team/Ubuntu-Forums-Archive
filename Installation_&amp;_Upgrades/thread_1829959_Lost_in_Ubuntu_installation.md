---
title: "Lost in Ubuntu installation"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2011-08-21
I want to install Ubuntu 11.04 along my current Windows XP installation and I am trying to figure out the following:

1. How to recognize the relationship between Windows disk drive letters and the Linux disk drive indicators like /dev/sda/

2. How to configure the multi boot?

3. Where to place the Linux swap file?

4. Which Linux filesystem is the best for general use?

The specifics:

Pair of identical Seagate SATA2 80GB drives partitioned in Windows as follows:

Drive 0 ntfs
C: 25GB Windows boot drive used 10GB for OS & software, no data.
D: 25GB used 3GB My documents data
Z: 25GB used 20GB data

Drive 1 ntfs
M: 25GB used 12GB data
L: 25GB used 3GB data
K: 25GB empty

When looking through the Ubuntu installation to be configured, 
I assume that drive 0 is /dev/sda where I have 3 partitions sda1, sda5, sda3. Drive 1 would be /dev/sdb with partitions sdb1, sdb5, sdb3 and I am not sure which corresponds to the Windows drive letters.

I would like to dedicate the empty drive K: for the Linux installation, swap space & data, and use minimal amount of space of drive C: for the dual boot.

Advice is most appreciated.
Thanks

---

### Post by fdrake on 2011-08-21
+to check your disk/partitions
use a live cd and go to menubar > system > administration > gparted
and you'll see 2 drivers 0,1 with the rispective partitions

or simply open the terminal from menubar > accessories> terminal and type

```
sudo fdisk -l
```
(i am not sure if the live cd need sudo .. just in case)
--------------------------------------------------------------------

+installation:
the easiest way would be installing automatially ubuntu with win in the first disk (with the swap partition) and after the installation use gparted to format the free space in the second disk  into ext2 or ext3. their both very similar, the second one has a journal which make disk-checking faster.And use the partition for saving your data or media.

---

### Post by spiky001 on 2011-08-21
+1 Gparted. A screen dump would help as well

---

### Post by dino99 on 2011-08-21
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by fdrake on 2011-08-21
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

i do mostly agree with you but not about the swap size . that should be relative to the ram of the computer. Does not make sense to have a swap of 4gb if your ram is 250MB?  it will make all the proccess slower in the and...

---

### Post by ineuw on 2011-08-21
Thanks for all the help. Ubuntu is up and running fine!

After careful analysis of Ubuntu's installation preferences, I realized that Ubuntu prefers to be installed on /dev/sda1 AND suspected that the NTFS format forces Ubuntu to make undesirable installation selection and presents incomprehensible options for a newbie.

However, it configures itself very neatly if there is an unformatted partition. I booted into Windows XP, moved the data from my D: drive on /sda1 to /sdb1 and deleted the partition. Ubuntu instantly recognized the unallocated drive and installed itself as I wished, with no questions asked and now the universe is as it should be. Thanks again.

---

