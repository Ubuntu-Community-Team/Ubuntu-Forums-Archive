---
title: "Ubuntu 14.04 installer does not recognize free space on a ntfs win8/bios drive"
date: 2015-08-07
forum: Installation &amp; Upgrades
---

### Post by carlos59 on 2015-08-07
Hello All.

I am trying to install Ubuntu on a pre-existing windows 8.1 system. I left 100 giga free on the harddrive, I created that partition using windows 8.1 and formatted it. but ubuntu installer says used unknown windows loader for the whole drive. If I use linux gparted it see the 2 partitions, is there something I can do to allow the installer to see that partition? do you think it might be related to the fact I did not install win 8 using uefi? 

thanks for any help.

---

### Post by ubfan1 on 2015-08-07
Did you use MSDOS or GPT partitioning on your disk?  The installer should be able to take the free space and make the partitions it needs, (default root and swap), but if you use MSDOS partitioning, you have a limit of 4 primary partitions, so that might cause some issue (but I thought the installer would just make logical partitions if it could).  If you already have 4 primary partitions, no more may be made from any free space, you'd have to back up and delete one.  Then the installer should make an extended primary, and add logical parititions there.

---

### Post by oldfred on 2015-08-07
Ubuntu cannot use Windows formatted partitions. Probably best to just delete it, and let Linux create the types it needs.

Post this from terminal in live installer:
sudo parted -l

---

### Post by carlos59 on 2015-08-10
thank you for taking the time to answer. after all I had the problem resolved, may be not the right way, but I just replaced the Ubuntu installer cd that I was trying to use (14.04) by the 15.04, and it asked me the magical question, install along with windows for which I replied yes, and it installed Ubuntu. Here is the result of sudo parted -l. What is the draw back of this set up of mine?

Model: ATA Crucial_CT240M50 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs
 2      368MB   126GB  125GB   primary   ntfs            boot
 3      126GB   240GB  114GB   extended
 5      126GB   236GB  110GB   logical   ext4
 6      236GB   240GB  4282MB  logical   linux-swap(v1)



thanks again

---

### Post by oldfred on 2015-08-10
That is the standard partition scheme most end up with.  And for a new user that is fine.

More advanced is a separate /home. And then even more advanced is separate data partition(s). With either you may  then only need 25GB for / as all your data is in other partitions. 

But I usually suggest a separate NTFS shared data partition as it usually is best not to write into the Windows NTFS system partition. Then you can set system as read only and have the shared data as read/write. Or have Windows have a smaller system partition and most data in another partition.

If you ever think about updating to Windows 10, be sure to backup partition table showing sectors. Windows reinstall or major upgrade forgets to rewrite partition table's Linux partition or your sda5.

---

