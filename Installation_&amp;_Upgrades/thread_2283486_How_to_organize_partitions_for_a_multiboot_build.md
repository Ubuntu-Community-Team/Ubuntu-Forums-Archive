---
title: "How to organize partitions for a multiboot build?"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by Xayide on 2015-06-22
Hello everyone! :D

English is not my native, so excuse any grammar error please!

I have a 1TB hard drive I want to partition to install Ubuntu. Now I have a 250GB partition for windows (and its corresponging 100MB partition reserved for the system). 
What I want to do is to install Ubuntu 14.04 in a different partition of 250GB, so I would leave 500GB unused space (250 windows - 250 Ubuntu) or so. The problem is that I've been reading some topics to see how can I do this and I don't really understand the process.  I've read this:
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
the "Partitioning scheme for multiple systems" part. 
I'm on my windows now, with the disk manager open. I have a 100MB partition and a 250GB partition for windows as said, and the rest is unassigned space. How should I partition that space for my Ubuntu installation? Just a single partition 250GB in size? Make different partitions to allocate /, /home, etc on them or should I wait to be in the Ubuntu installation to do this? 
I will say too tham I'm pretty new with linux installation. The only linux I've had was a non-graphic Debian 7 to learn use some simple commands, and it was on a virtual machine so it was not difficult to install.
Last week I tried to do this dualboot, and what I did was partition the disk as said: 250GB for Windows and 250GB for Kali, and while installing the Kali, in the partitioning menu I didn't know how to tell him to install himself in the partition I made for him, and I accidentally told him to use all the disk so I erased my Windows.
Thank you much and hope you can help me! :D

---

### Post by grahammechanical on 2015-06-22
Ubuntu can run fine on just two partitions - one for Ubuntu and one for swap. Some of us have a partition for /home because a re-install if done carefully will not remove our data files and our user configuration files. Some of us also have a partition just to keep our data on. Some of us have a partition for data that is formatted NTFS so that both Ubuntu and Windows can access the data. It really is up to us.

Ubuntu will run nicely in 7 GB to 10 GB of disk space but if /home is a folder in that partition there will not be much space for large files or installing non-default applications especially if they are large programs. To put it another way, Ubuntu does not need 250 GB of disk space. 25 GB would be more like it.

A separate partition for /home would be useful but it does not need to be massive if we are going to have a separate partition for data. A separate partition for data would really be useful and make it as large as you want. Two data partitions - one NTFS and one Ext4 might also be useful. The sizes would be up to you.

As for swap, well that all depends on whether you will use hibernation (suspend to disk) in which case you will need a swap partition larger than the size of RAM. Otherwise, the greater the RAM size the less likely that swap will be used. So, the swap partition can be kept small.

Whether you need a boot partition will depend on whether you will encrypt the installation or use LVM and also Whether Windows is Windows 8 on a UEFI boot system.

All of these partition sizes can be adjusted after installation. We use a live session and the Gparted utility. But it is useful to already create the partitions we want and need before installing. Then we can use the Something Else option to identify the Ubuntu partition (mount / ) and the Home partition (mount point /home) and the swap partition mount point /swap) but not the Data partition. There is no facility in the installer to do that.

All of this information is general and not specific to your use case.

Regards.

---

### Post by yancek on 2015-06-22
You have not indicated which windows you are using.  If you are using windows 8 and UEFI, booting will make a difference and you would need to install Ubuntu UEFI to save yourself a lot of headaches.  The 100MB windows partition you refer to is most likely a boot partition and you are probably not using UEFI.  Don't disturb either windows partitions.  I would just create one 25-30GB partition on which to install the Ubuntu system and then create a partition or partitions withe rest of the space for data.  You can use ntfs as the filesystem and then will be able to access from either windows or Ubuntu.  This would be the simplest but it's basically a personal preference.

Make sure you select the "Something Else" option in Ubuntu as that will give you some control over the install.

---

### Post by Xayide on 2015-06-22
Okay, so what I could do is now in the Windows 7 disk manager, I would first of all have my windows partitions (250GB and 100MB) which I would not touch, and then I could create another big partition for data storage (that NTFS that both Windows and Linux can read so I can access it from both of them). Another partition for /home not too big (25GB as I already have the data partition), one for / (10GB maybe?) and one for /swap that varies according to my RAM (now I have 8GB, but maybe I add another 8GB card to make a total of 16, so maybe 5GB swap partition would be ok?)

So the basics are: 
· One big NTFS partition for data from both Windows and Linux
· One small partition for /
· One bigger (but not as big if you have a partition for data) partition for /home
· One /swap partition that varies according to your RAM amounr (the greater the RAM, the lower the swap?)

Another thing is that I've been exploring the installer, and it doesn't detects my partitions. It says that I have one big 1Tb partition and nothing else, and I don't know why. I've been looking and I've seen that it could be a missconfiguration between MBR and GPT partitioning, which I don't understand at all. What could I do to fix this?

---

### Post by oldfred on 2015-06-22
Post this from terminal in live installer:
sudo parted -l

Was this a Windows 8 system that you reinstalled Windows 7? Windows 8 uses gpt and default install from Windows 7 is usually BIOS with MBR(msdos) partitioning, but Windows does not convert correctly. There is an easy fix if that is the issue. 

If only making /home 25GB I might keep it inside / (root) and just make / larger. I have all data in my data partitions and use about 10 to 12GB of my 25GB / partition including /home. I do have .wine installed which is in /home and is about 2GB on its own for Picasa, otherwise /home's settings are very small. But you do need to configure so data is automatically in data partition(s).

Swap really should only be one of two sizes. The same as your RAM in GiB (not GB) or 2GB. And only the larger size if hibernating and hibernating is not recommended when dual booting. Actually Ubuntu boots so fast with newer systems that hibernation does not save much.

---

### Post by Xayide on 2015-06-22
The output is:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10JPVX-16J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number        Start         End         Size       Type         File system      Flags
1                 1049kB      106MB     105MB    primary     ntfs                boot
2                 106MB       262GB     262GB    primary     ntfs




Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GU90N (scsi)
Disk /dev/sr0: 1044MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac


Number    Start        End         Size           File system    Name    Flags
1             8192B      24.6kB     16.4kB                          Apple
2             42.3MB    51.8MB     9568kB                         EFI





No, it wasn't a Windows 8, the laptop is brand new and came without OS. I installed a Windows 7, and then tried to dual boot with Kali. Accidentally erased my Windows and left only Kali, so I erased all partitions and reinstalled windows 7 in a 250GB partition, leaving all other spaced unassigned.
I didn't know how to maintain the output structure so I upload a snapshot of what it looked like.

[IMG]http://oi58.tinypic.com/2ikrrq8.jpg[/IMG]

---

### Post by oldfred on 2015-06-22
I am not familiar with Mac, but you flash drive or DVD looks like a UEFI installer for a Mac, not a standard PC installer.
If a Mac type installer with UEFI then it will want gpt partitions, which will  not work with your Windows installed in BIOS mode. Windows in BIOS boot mode must have MBR partitioning.

---

### Post by Xayide on 2015-06-22
No, I'm not using Mac. This is the Laptop:
[http://www.pccomponentes.com/fujitsu_lifebook_ah544_g32_i7_4702mq_8gb_1tb_gt_720m_15_6_.html](http://www.pccomponentes.com/fujitsu_lifebook_ah544_g32_i7_4702mq_8gb_1tb_gt_720m_15_6_.html)
I don't know what I did, but the problem somehow solved. It detected the partitions, but not the windows. I Installed ubuntu and everything, but not GRUB screen to select which one to use when booting appears.

---

### Post by oldfred on 2015-06-22
Is it booting directly into Ubuntu?

If so run this:
sudo update-grub

---

### Post by Xayide on 2015-06-23
No, it was running Windows first. I gave up and directly installed Ubuntu, I'll go and learn some things before doing the dualboot again.

---

