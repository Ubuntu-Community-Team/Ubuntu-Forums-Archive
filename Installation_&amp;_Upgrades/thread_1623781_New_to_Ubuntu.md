---
title: "New to Ubuntu"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by JayHaloBeast on 2010-11-17
Well, as it says in the title; I'm new to Ubuntu. Well, I'm new to multi-OS systems altogether. So, I've come here for help and just for someone guide me through the process of this.

As I currently type this, I'm downloading the Ubuntu 10.10 AMD64-bit OS. I'm going to install it via USB Flash Drive, I know how to change the boot order and all that. But, here's what I'm a bit confused about. I've got two partitions on my HDD. My 990 partition (C: ) and my 10 GB partition (B: ) - I want to install it to (B: ), will I have a simple option of installing it to (B: ) when I run the installation? 

Also, once it's done installing how will I select Ubuntu to start-up instead of Windows 7. I still wish to keep Windows 7, just I when I wanna use. Will it be like a multi-Windows OS system where it has the list:

Windows Vista
Windows 7

Or will it be something different? 

Thanks in advance!

---

### Post by sikander3786 on 2010-11-17
Welcome to Ubuntu and the forums :popcorn:

> will I have a simple option of installing it to (B: ) when I run the installation? 

From the Ubuntu installer's partitioning page, choose Manual partitioning. You'll see both your drives name something like sda1 and sda2. Delete your 10GB drive and create 2 partitions in the freed up space.

1. Ubuntu Root partition. Format ext4, Mount Point = /, size = 9 GB

2. Swap parition, Mount point = Swap

And you'r done.

> Will it be like a multi-Windows OS system where it has the list:


After the installation is completed successfully, you should be able to switch between Windows and Ubuntu from the Grub menu that appears right after Bios screen.

Sometimes, there have been issues where Grub doesn't detect Windows 7 (very rare). If you want to be sure that you are not going to run into problems, you can post the output of bootinfoscript from Ubuntu Live CD as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

That will help use better understand your setup and if you need to do something to the Windows 7 boot files, do it prior to the installation of Ubuntu so you don't run into problems.

---

### Post by azertyh on 2010-11-17
hello,
read the doc about the installation [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
and the doc about dual-boot [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)

---

### Post by matt_symes on 2010-11-17
Hi

10 GB is not very much space for the Ubuntu partition. I would be tempted to give it more, after all windows has 990GB. If you do decide to do this use the windows tools to shrink the windows partition.

As has been stated, you will need a main root partition and also a swap partition. If you use hibernation then the size of the swap partition should be at least the size of your RAM plus a bit extra as during hibernation the RAM is written to the swap file. You might also consider a home partition.

Welcome to Ubuntu.

Kind regards

---

