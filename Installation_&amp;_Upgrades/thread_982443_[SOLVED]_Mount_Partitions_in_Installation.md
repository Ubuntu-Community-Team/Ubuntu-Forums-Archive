---
title: "[SOLVED] Mount Partitions in Installation"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by jtan189 on 2008-11-14
I have attempted to search for answers to this problem, but have not found anything that seemed to directly apply to my question.

I plan on partitioning my hard drive beforehand to my actual Ubuntu installation (I'm running only Vista Business at the moment). I have a particular scheme I'm gonna try to pull off, involving logical drives.

From a forum in NBR:
> If you create all the Linux partitions beforehand, let's say three partitions for /, swap, and /home, then you have to choose the "manual install" option in the Ubuntu installer, then you have to know how to mount each partition correctly. This is NOT HARD, but the first few times you'll feel lost. I did it over and over several times on a practice PC. Now it's fun!

I was hoping someone could tell me or direct me to a place where I could find out how to mount these partitions. I have no idea how to do it and I don't want to screw up my computer by experimenting. Also, just a side question - will the Ubuntu installer ask me where to place the /home partition? I want to have it on a separate partition from the primary Ubuntu installation partition.

---

### Post by Rocket2DMn on 2008-11-14
Do you plan on using a dual boot setup with Ubuntu and Windows Vista?  A typical Ubuntu installation only requires 2 partitions - the root (/) and swap (no mount point).  Your swap partition should probably be 1.5x-2x the size of your RAM.

Having a separate /home partition is optional, and convenient, esp. for beginners who are more likely to screw something up on the filesystem and have to reinstall.  (My advice there - if you don't know what you're doing, don't do it!  Ask us first!)  Having a separate /home partition means all your personal configuration and data are stored on a separate partition from the root filesystem.  If you choose to use a separate /home partition, it will be the largest.  So let's consider this dual boot setup with Ubuntu + /home partition and Vista.

partition 1 (real): Vista backup partition - NTFS
partition 2 (real): Vista regular partition - NTFS
partition 3 (real): Ubuntu linux root partition (say, 10 GB, a default install uses about 4GB) - EXT3
partition 4 (extended partition) - Extended
partition 5 (logical, meaning inside the extended partition) - /home (most of the rest of the hard drive) - EXT3
partition 6 (logical, inside the extended partition) - swap (1.5x-2x your RAM capacity) - SWAP

You will need to use manual partitioning with the installer.  It will not specifically prompt you for /home, you have to create the partition then tell it to mount there.

You will need to resize Vista's NTFS partition first - PLEASE BACK UP YOUR DATA BEFOREHAND.  Defrag the drive before you boot into the installer CD to resize.  During the partitioning process you will shrink the Vista partition, then proceed to create the new ones for Ubuntu.

---

### Post by jtan189 on 2008-11-14
Thanks for the quick reply.

Yeah, I do plan on dual-booting between Vista and Ubuntu. Here's the scheme I had in mind:
[LIST]  
[*]primary partition for Vista (with NTFS filesystem)
[*]primary partition for Lenovo (S) partition
[*]primary partition for personal data and files (documents, musics, pictures, videos, etc.) To be used for storing stuff from both Ubuntu and Vista. (with NTFS filesystem)
[*]extended partition (itself partitioned as follows):
[LIST]
[*]logical partition for /home
[*]logical partition for /
[*]logical partition for swap space
[/LIST]
[/LIST]

I'm doing this on the new Lenovo ThinkPad T400 that I just got. It came with three partitions. One for the C drive, one backup partition ("Lenovo", Q), and one partition called "SERVICEV003" with the letter "S" identifying it. Clicking on that partition basically tells you to leave it alone, as it is important for stability in my T400. I've made recovery discs, so I plan on deleting the backup "Q" partition. Unfortunately, I'll have to keep the S partition around, as well as leave it as primary (since that's what it is set as).

I was planning on creating all these partitions (after defragging my Vista partition) using Acronis Disk Director. Then I wanted to boot into the Ubuntu LiveCD and install Ubuntu using the manual method. I'm totally clueless of how to tell Ubuntu to assign SWAP, /home, and / to the specific partitions I created beforehand though. And then something about mounting partitions got mentioned... I just want some sort of security in the form of knowledge as I go into this process.

---

### Post by Rocket2DMn on 2008-11-14
That looks like a good layout.  I suggest just using the LiveCD to do the partition layout - GParted is available under System->Administration->Partition Editor if you want to setup the partitions in advance of the install process.  Otherwise you can do the resizing and partition layout at the beginning of the install.
During the install it will ask you how to partition the disk and you will select the manual option.  Then it will show you the existing partitions and you choose whether to format them and tell where to mount them (just select the partiton and click choose to edit it, I'm not sure on the exact option name).  You also have the option to delete partitions and create new ones.  Swap has no mount point, so it will gray that box out.  You will tell it to mount you root filesystem at / and the separate home partition at /
You might also be able to tell it where to mount the windows partition, but if you are afraid you will screw it up, just leave that partition completely alone and it will say that its not changing it.  Before the installer proceeds it will list the partitions that are beind adjusted/used, and you will have to confirm the changes.
You seem knowledgable enough that I don't exepct you will have problems.  If you ever feel like you might be screwing it up, then just ask for help.  Don't proceed until you are ready.

---

### Post by jtan189 on 2008-11-29
So it all turned out well. I have my hard drive partitioned as I planned and was able to install Ubuntu without any problems. Thanks for the help Rocket2DMn.

---

