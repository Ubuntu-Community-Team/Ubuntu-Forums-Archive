---
title: "starting from scratch"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by stldirty on 2008-06-09
ok i'm bout to start from scratch installing hardy again on my laptop.  i have a backup of my old setup but its causing too many problems.  so ok, i'm starting from scratch.  i hear that i should make a seperate partition for my /home directory?  how do i do this and what's the recommended size for the home partition?  also i already have vista installed.  if i wanted to install hardy 32 bit AND hardy 64 bit would this be a problem?  would i need seperate swap and home partitions for each?  is there a limit to how many partitions i can havve on sda drives?

thanks in advance.

---

### Post by talktoari on 2008-06-09
Since you are starting from scratch and have Vista already installed, here is what I recommend:
1. Boot with windows Vista and choose "Administrative Tools" -> Computer Management -> Disk Management
2. Choose a partition and right click to do a "Shrink Partition".
3. Provide a size of the shrinking partition to have around 6-10 GB or any space created for your Ubuntu installation.
4. Once shrinking is complete, you will see that space marked as "Unallocated" in your partition.
5. This space will be where you will be installing Ubuntu.
6. Insert your Ubuntu CD in the CD/DVD ROM drive and shut down the computer.

Ubuntu Installation:
1. Start the machine with boot CD in your drive.
2. Follow the steps for installation.
3. While an option for partitioning comes up during the installation process, choose the option "Choose maximum contiguous space" or something similar to this option. This will actually choose ur "Unallocated" space for installing Ubuntu.
4. Go ahead with the installation and there you are with your new install of Ubuntu Hardy heron.

Enjoy the Ubuntu OS.

Hope the above helps.

---

