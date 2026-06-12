---
title: "Installing Ubuntu 7.10 on second Hard Drive"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by rsjbuntu on 2008-03-17
Hi all

I'm trying to install Ubuntu on the second hard drive of the computer. The reason for this post is that I had tried to dual boot earlier but could not boot into XP from GRUB and had to reinstall XP from scratch. As I have collected a lot of data on the main hard disk now, I cannot risk another clean reinstall.

My specs are:
-------------------
Intel Core 2 Duo 2.2 G Hz
945 Mainboard with built in video, sound, network
2 GB DDR II RAM
1 SATA HD 160 GB
1 SATA HD 250 GB

The primary HD right now is the 160 GB and that has XP pro installed on it. 
The second HD which is the 250 GB is the one I want to use to install Ubuntu.  This HD is clean (unformatted). Could anyone walk me through installing Ubuntu on this HD as I do not want to mess up again. I have looked into the forum but could not find any post which deals with this configuration. Any help will be much appreciated. Thanks.

---

### Post by Rocket2DMn on 2008-03-17
Here are a number of links to help you out:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs) - you just have to be careful to install to the correct HD.  You can tell because your windows drive will have ntfs partitions.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by mikewhatever on 2008-03-17
There was nothing wrong with the previous installation, and you shouldn't have reinstalled XP, but should have asked for help then. To make sure your XP is safe, the best practice is to disconnect it if possible, then install Ubuntu (regular installation, nothing special), and then, add an entry for XP to GRUB.

---

### Post by rsjbuntu on 2008-03-17
Thanks Rocket2DMn for the links......I will look into them....and mikewhatever could you tell me how to add the entry for XP in GRUB once I have installed linux?

Sorry to be a baby but I really am at my wits end!! :confused:

---

### Post by mikewhatever on 2008-03-17
> **rsjbuntu said:**
> ...and mikewhatever could you tell me how to add the entry for XP in GRUB once I have installed linux?

Sorry to be a baby but I really am at my wits end!! :confused:

A little more info is needed. Can you post the outputs of the following:
<sudo fdisk -l>
<cat /boot/grub/device.map>
<cat /boot/grub/menu.lst>

---

