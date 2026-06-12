---
title: "Dual boot with windows - recommendation needed"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by kunalv-shah on 2018-08-29
Hello,

I have ubuntu 18.04 installed on my desktop. Below is link for my boot-info file. 

[http://paste.ubuntu.com/p/SFFv7ntHBs/](http://paste.ubuntu.com/p/SFFv7ntHBs/)

Basically I have 3 partitions.

Part 1 - efi
Part 2 - SWAP
Part 3 - physical - LVM2 - in physical I have logical partition for /home partition for / and partition for *other*.

Now I want to make space for Windows 10 partition. I want to allocate some space out of existing setup and configure dual boot. Before I proceed, I want to check if you can give me some recommendations about how to get appx 100 GB free space for Windows 10 installation and how should configure dual boot once Windows installation is completed. I know once Windows installation is completed, I will lose grub so I need to restore that later for dual boot.

the partition /dev/mapper/linux-other 2bed251f-4e81-4aad-b274-193695251205   ext4 
[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -R /dev/mapper/"[/COLOR] output: [COLOR=#666666]=========================[/COLOR]

/dev/mapper:
control
linux-home
**[COLOR=#ff0000]linux-other[/COLOR]**
linux-ubuntu18
(highlighted in red - linux-other) you will see in boot-info is the one I want to use. It is not used right now (although formatted as ext4). 

Thanks in advanced
Kunal Shah

---

### Post by yancek on 2018-08-29
Comparing your post to the boot-info file is a little confusing.  You only refer to one drive in the post but boot-info shows you have 3 1TB drives.  You have windows boot code in the MBR of two drives (sda, sdb) and you have EFI partitions on two of the drives (sda and sdc) so I am guessing, since the Ubuntu EFI boot files are on sda1, when you boot it finds those files which point to the main Grub boot files on sdc3 and boots.  Your sdb drive already has a windows partition taking up the entire drive.  Is that a data partition?  Which of the 3 drives were you planning to install windows 10 to.  Is it sdc where you have your Ubuntu?  Since you have LVN on that drive, I believe it is possible to resize/shrink an LVM partition with GParted which is also on the Ubuntu installation disk.   You will need to read up on that or get advice from others as the standard resize method used by GParted will not work on an LVM system.  I can't help as I've never used LVM.  Good luck.

---

