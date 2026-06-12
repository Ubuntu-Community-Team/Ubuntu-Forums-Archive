---
title: "Ubuntu 9.10 - Mount-points spread over 2 disks for optimal performance question."
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Mandragara on 2010-02-17
I have a 2.66GHz C2D, 4GB RAM, two 400GB SATA2 HDDs and one 120GB SATA1 HDD. Recently a fellow geek recommended the following partition layout for optimal performance in our beloved distro. Usage will be many applications installed and large media files kept in home with a file, bittorrent and web server running.

--
HD0 (400GB)
/boot EXT2
/root EXT4
/sbin REISERFS
swap (2048MB)

HD1 (400GB)
/home XFS
swap (2048MB)
/bin REISERFS
/etc JFS
/lib EXT3
/opt REISERFS
/tmp XFS
/usr EXT4
/var EXT4

HD2 (120GB)
/windows NTFS
--

Is this configuration optimal? I have been researching File-systems and the like but I am just a little too inexperienced to make a definitive judgement on the matter. Is there REALLY a benefit to all these different partitions and FS's? If not what do YOU recommend.

Thanks :D

---

### Post by b0b138 on 2010-02-17
No it is not....WAYYYY too complicated.  Every different filesystem would have to have its own partition.  So HD0, would end up with 4 partitions and HD1 would have 8 or 9.

You also only need 1 swap partition, not 1 on each drive.

---

### Post by Mandragara on 2010-02-17
Two swap partitions is supposed to provide optimal I/O performance and all the partitions can be logical.

---

### Post by ajgreeny on 2010-02-17
> **b0b138 said:**
> No it is not....WAYYYY too complicated.  Every different filesystem would have to have its own partition.  So HD0, would end up with 4 partitions and HD1 would have 8 or 9.

You also only need 1 swap partition, not 1 on each drive.
+1

I can see no good reason for such an incredibly complicated setup, and the number of hard disks being used/accessed does not have to make things so difficult.  How would you ever remember what was what when doing any partition management of any sort?  You could quickly mess things up so easily with such a system.

Go for one swap of 4GB if you need that much, a root partition 10GB of ext4,  a separate /home partition 5GB ext4, and finally a /data partition (the rest of the disk as ntfs), all on hd0, ie sda1, sda2, sda3 and sda4.  Make sure all your data files, ie docs, music, videos, photos, etc etc is in one of the /data partitions available, not direct into /home

Hd1 should be left as one, or maybe two partitions, either as ntfs if you want to share with windows or ext4, if only for linux,

Leave windows where it is but again you could make part of that disk a separate /data partition if you wish on ntfs.

All data partitions can be now accessed from windows, and by adding them to the ubuntu fstab, from ubuntu as well, ubuntu being able to read and write to ntfs partitions, whereas windows can not do the same to ext4 partitions.

I suspect your fellow geek friend was just trying to impress you with his great knowledge of linux and partitioning, but I have to say, I am not at all impressed with his suggestions.

What's wrong with KISS?  (*Keep it simple, stupid.*)

---

### Post by snkiz on 2010-02-17
Wow Thats a lot of headache for not much gain. I have mixed partitions on my box (Not as extensive as what your proposing.) And I wish I never did it. Riser has had errors ever since my first hard boot that wont go away. It also complicates trouble shooting.
 You don't have partition sizes mentioned? keep this in mind, if you make say /sbin 50gb and you only use 10gb that other 40gb will be wasted, you cant reallocate it latter. (Not simply anyway.)
 You do not need a swap on each drive, one will suffice at 2x your ram. Put it on your fastest drive where ever the drive heads rest. (beginning or end of the drive depending on what kind it is.) and put your /root on the other drive.
 /var is mostly temp storage so it needs to be variable. /bin, /opt, /usr, are where most of the program data is stored (Via synaptic/.deb installs.) So set these only if you know how much your going to install and you not planing on adding anything. /sbin and /boot is for system tools that in my experience don't change much from install IMO it would be safe to separate these with a healthy cushion. 
 Thats the main problem with separate mount points in the file system. Once you do it your kinda stuck, unless you want to start over. Plus the huge headache of keeping track of all that at upgrade time. I would suggest a simpler setup such as this using an lvm for /home so you can maximize your disk usage for data and still have flexabilty in sizing.

hd0 (400gb)
256mb ext4 /boot (Enough room for four kernels.)
100gb  ext4 /root (This includes /var /sbin /bin /usr /opt etc.)
rest of drive make an lvm partition that you will use for home.

hd1 (400gb) *lets say for this example this is the fast drive*
2x ram   swap (You only need it this big if you want hibernate to work.)
rest of drive make an lvm partition that you will use for home.

hd2 (120gb)
min 15gb NTFS Windows install (mount in Linux if desired at your preference.)
10gb fat32 /winshare (like an internal usb stick to transfer files to windows, optional.
25gb unallocated (to test and play with. optional)
rest of drive make an lvm partition that you will use for home.

Your Lvm can use witch ever FS you like. ext4 would be the simplest. You really don't want to experiment with you /home partition, its the one your going to keep in future upgrades.

---

