---
title: "Cannot boot from external HDD after installation-Error: File not found, Grub_Rescue&gt;"
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by Super Stupid Idiot on 2012-08-29
Hi,

I have installed the ubuntu on my external hdd but when I tried to boot from it, it shows ->

Error: file not found
grub_rescue>

I tried to navigate using ls, and find that the grub_rescue cannot find the grub folder in my /boot directory. But when I boot into the live cd and navigate using the explorer I can find the grub folder in the boot directory.

May I know how could I resolve this issue? My internal hdd is installed with windows 8.

Also, for the installation I partitioned 2GB of swap and the remaining is root '/'. The bootloader I chose the external disk. I have tried unintalling and installing several times but the same thing appears. :(

Please help! Thank you a lot!

---

### Post by oldfred on 2012-08-29
Welcome to the forums.

If your external is very large that may be part of the issue. Some systems or grub seem to have issues with very large / (root) partitions. Some have fixed it just by shrinking the / partition and using the rest of the drive as /home or as data partition. Boot-Repair suggest a separate smaller /boot partition which also works.

Post link to Bootinfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Super Stupid Idiot on 2012-08-29
> **oldfred said:**
> Welcome to the forums.

If your external is very large that may be part of the issue. Some systems or grub seem to have issues with very large / (root) partitions. Some have fixed it just by shrinking the / partition and using the rest of the drive as /home or as data partition. Boot-Repair suggest a separate smaller /boot partition which also works.

Post link to Bootinfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Hi, thank you! I followed what you said and this is the report: [http://paste.ubuntu.com/1174459/](http://paste.ubuntu.com/1174459/)

BTW, I tried to reinstall grub with the boot repair but it's still the same. Most probably like what you mentioned - my hdd is 500gb.

Should I reinstall again with a specific boot partition? If so, how should I specify all the partition based on the 500gb space? 

Thank you a lot!

---

### Post by oldfred on 2012-08-29
You can do a separate /boot, but if / (root) is smaller and all in the first 100GB we have not seen issues. I use 25GB and have multiple installs. Then I use data partition(s) for all my data. I have a shared NTFS to use data with both my old XP and all my Ubuntu installs and a ext3 data partition where all my newer data now goes. If not wanting a Linux data use a separate /home.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB total:

Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Since you do not have a lot of data in your / partition you can do a quick experiment. I found this suggest works at least 50% of the time, but many just reinstall. You can just shrink / (root) with gparted,  so it is entirely inside the 100GB of the drive. If it then boots you can either move /home or use rest of space as a data partition or reinstall and know it will work.

---

### Post by YannBuntu on 2012-08-30
Hello

> **Super Stupid Idiot said:**
> Hi, thank you! I followed what you said and this is the report: [http://paste.ubuntu.com/1174459/](http://paste.ubuntu.com/1174459/)


This confirms what Oldfred guessed: your Ubuntu partition (sdb1) ends far (~500GB) from the start of the disk.

You can either:
**1) via Gparted reduce sdb1 from 500GB to 100GB** (reduce it from the right-side, so that it still starts at the beginning of the disk). In the 400GB free space that will be created, you can create an EXT4 partition where you can put documents/videos/pictures..
**2) OR you can create a little /boot partition at the start of the Ubuntu disk** ( [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) )

---

### Post by Super Stupid Idiot on 2012-08-30
Hey thanks to both of you! I now can finally boot after partitioning like the following:

Primary partition, 500mb ext4 for /boot
Primary partition, 20gb ext4 for root /
Primary partition, 5gb for swap
Logical partition, 200gb for /home
free space remaining 300++ gb
total space = 500gb~

But now I got another issue: that is after boot, the system says serious errors were found while checking the disk drive for /home

Press I to ignore, S to skip mounting and M for manual recovery

What could I do now? If I press S, the ubuntu loads but pop up some messages and then stay empty?

Thank you a lot!

---

### Post by oldfred on 2012-08-30
If it is sda5 run this or change to correct partition.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

To be able to create more partitions you will have to expand the extended partition to include all of the unallocated. Then you can create as many logical partitions as you want.

---

