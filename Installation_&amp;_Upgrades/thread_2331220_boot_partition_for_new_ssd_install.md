---
title: "/boot partition for new ssd install?"
date: 2016-07-19
forum: Installation &amp; Upgrades
---

### Post by Thomas_Price on 2016-07-19
I'm currently running 12.04 on a HDD(which I am keeping for storage), but am adding a 500GB SSD and am going to install 16.04.

How do you suggest I partition the disk?
[LIST=1]
[*]Do I still need to create a /boot partition in 16.04?
[*]Should I create a separate /home partition on the SSD, or leave /home in the same partition as / and symlink to the storage folders on the HDD or a separate partition on the SSD?
[/LIST]

Any other advice on drive setup?

Thanks,

Tom

---

### Post by Dennis N on 2016-07-19
You don't need a separate /boot partition, but if you do, have an adequate capacity (perhaps 400 - 500 mB) and keep an eye on it to remove excess kernels - most users retain the most recent two and remove the rest. 

The SSD is the disk you will boot from, so all OSes you install belong on it. That is the main thing. Whether you make a separate home partition is up to you. 

My setup is SSD (internal) + HDD (eSATA). All OS installs go on the SSD. Partitions 2,4,5,7 are Linux installs. No Windows here. I use the HDD (sdb below) for my own files to be accessible to each OS while it is used. No separate home partitons. Don't see the need for those, but add them if you like. Most documents & other files I might store in a home partition are on the data partition instead so all OS can access them in common.

```
dmn@Zotac:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0    80M  0 part /boot/efi          EFI System Partition
&#9500;&#9472;sda2   8:2    0  24.4G  0 part 
&#9500;&#9472;sda3   8:3    0   3.9G  0 part [SWAP]
&#9500;&#9472;sda4   8:4    0  24.4G  0 part 
&#9500;&#9472;sda5   8:5    0  24.4G  0 part 
&#9500;&#9472;sda6   8:6    0    80M  0 part                    EFI System Partition 
&#9500;&#9472;sda7   8:7    0  24.4G  0 part /
&#9492;&#9472;sda8   8:8    0    80M  0 part                    EFI System Partition 
sdb      8:16   1 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   1 117.2G  0 part /mnt/Common-Files

```

---

### Post by oldfred on 2016-07-19
If only Ubuntu, I also suggest gpt partitioning. 
Even when I only had a BIOS computer I started adding both the ESP - efi system partition and the bios_grub partition, so I could later move drive to a new UEFI system and not have to totally reformat. UEFI recommends that ESP be first or near beginning of drive.

I have entire system in SSD, but link all data folders to a /mnt/data partition on my HDD.
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by Thomas_Price on 2016-07-27
Thanks - so I don't need a /boot partition, but I can have one.  What is the advantage of having it (as I do in my current setup)?  Is it that some motherboards have trouble booting without the /boot partition?

---

### Post by ubfan1 on 2016-07-27
It's more the BIOS not being able to address blocks beyond a certain limit.  An old problem when disks grew more quickly than firmware, but maybe becoming relevant with the 4T disks again.

---

### Post by Thomas_Price on 2016-07-27
Thanks!

---

