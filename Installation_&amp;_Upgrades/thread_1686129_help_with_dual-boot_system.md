---
title: "help with dual-boot system"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by bydotwanho on 2011-02-11
I tried to create a dual book system using Windows XP and ubuntu. I have a 1 terebyte hard drive partitioned into three partitions. I first installed Windows on the first partition and it ran flawlessly. However, when I installed unbuntu on the third partition, the ubuntu worked but I could not get back to Windows. 

The boot manager asked which partition I wanted, but it would only go to ubuntu. I finally erased the partitions and reformatted the hard drive, but now I can't do anything with the hard drive. That is, I can't get Windows to reinstall. 

I'm thinking that ubuntu wrote something in the MBR that Windows doesn't like, but I don't know how to get it out so I can start over. If I can have only one OS on this machine, it needs to be Windows because I'm building it for my husband.

Can anyone help me?

---

### Post by gnomey on 2011-02-11
I'm not clear what exactly happened, but to be honest, I'd say the best thing to do is to completely zero the drive, this will completely destory all the data on it to an unrecoverable state, but since you already tried to reformat the drive, I'm assuming this isn't a problem for you.

Here's a download link to Darik's Boot and Nuke:
[http://www.dban.org/download](http://www.dban.org/download)

It's probably a bit much to do to fix the problem, but it'll completely zero the drive, it'll be like a brand new one so will almost definitely fix the issue. If Windows won't install on that, theres something mechanically wrong with the drive then.

---

### Post by jerrrys on 2011-02-11
so your saying that the arrow key worked, but you could not enter into xp from grub boot menu ?

simply reinstalling ubuntu should restore the boot process provided your windows partition has not been altered.  don't understand the problem with xp not booting

---

### Post by Hakunka-Matata on 2011-02-11
As you're starting with a fresh hard drive, the installation of WindowsXP and Ubuntu is quite easy.  I would recommend installing WindowsXP first, and Ubuntu second.  If you want both XP and Ubuntu to use half of the drive, there's no need to create partitions before hand.  Let XP install, then install Ubuntu, Ubuntu will ask if you want to install the systems 'side by side' and it will reformat, resize the drive for you automatically.

---

### Post by oldfred on 2011-02-12
Windows seems to want either an empty drive or a NTFS partition with the boot flag.

You should be able to create a NTFS partition with the boot flag and then XP will install to that partition.

I prefer partitioning in advance for all systems, so I know what is where and that it is the size I want.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

