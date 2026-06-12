---
title: "Updating from 8.04 to 10.04 from CD"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by snhapratyush on 2010-09-27
I had Ubuntu 8.04 & Windows Xp installed on by 80GB Hard Disk by giving 40GB each to Ubuntu & Xp. Due to some problem in Windows Xp (nothing new) i had to reinstall Windows Xp. I had taken backup of all data on Windows & Ubuntu fully knowing that Grub would go haywire.

Now i want to install Ubuntu 10.04 on the 40GB that was earlier occupied by Ubuntu 8.04 from CD. But i dont know the procedure plz help me out.

I'm posting the output of sudo fdisk -l

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2611 20972826 7 HPFS/NTFS
/dev/sda2 2612 9729 57175335 f W95 Ext'd (LBA)
/dev/sda5 2612 3916 10482381 7 HPFS/NTFS
/dev/sda6 3917 5221 10482381 7 HPFS/NTFS
/dev/sda7 5222 5968 6000246 83 Linux
/dev/sda8 5969 6217 2000061 82 Linux swap / Solaris
/dev/sda9 6218 6919 5638783+ 83 Linux
/dev/sda10 6920 7621 5638783+ 83 Linux
/dev/sda11 7622 8323 5638783+ 83 Linux
/dev/sda12 8324 9025 5638783+ 83 Linux
/dev/sda13 9026 9729 5654848+ 83 Linux

Should i delete all Linux partitions ? What and how many partitions  (min.) should i make ? What partition should i use as mount ? Should i use ext3 or ext4 in all partitions ? 

How should i go about it ?

---

### Post by ajgreeny on 2010-09-27
Boot to the live CD and use the install icon as usual.
When you get to the partitioning part, choose **Specify partitions manually (Advanced)** and then when you get to the next page you will see the ext3 and swap partitions for ubuntu 8.04.  You can highlight these and edit them to be the new / (root) and swap partitions, or you can delete the old / and make a separate / and /home partition, as well as swap.  Everything else will be exactly as you have done before when installing.

Just make sure you avoid doing anything to your windows (NTFS or fat32) partitions and all should be well.

---

