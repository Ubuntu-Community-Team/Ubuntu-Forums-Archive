---
title: "Windows 7 then Ubuntu 9.10, No GRUB"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by mattgaunt on 2010-03-08
Heya Everyone,

I've been dual booting for years now between XP and Ubuntu Dapper -> Karmic so apologies if this is a stupid question.

My computer has a number of hard drives but on the main Hard Drive I have a Windows 7 partition and a Ubuntu Partition and a Swap partition.

I've installed Karmic on it's partition twice now, I know the disc is fine because I have checked it for errors and installed it on other computers.

I have tried setting up the Boot Loader from Windows 7, but this yields a message "Cannot load from harddisk". GRUB doesn't install what so ever.

Do I need to specify where GRUB gets installed as Windows 7 uses a different Boot Loader? Is this a Karmic / Windows 7 / Hardware bug?

Any suggestions would be greatly appreciated.

Cheers,
Matt

---

### Post by zvacet on 2010-03-08
> GRUB doesn't install what so ever.

Use procedure for reinstall grub2 described [here]("https://help.ubuntu.com/community/Grub2") and install grub on MBR.

---

### Post by mattgaunt on 2010-03-08
I have done a fresh install of karmic, so I am assuming that would of installed grub2 with it?

There seems little on the page about install Grub2 from the live CD  for an installed system when you can't get access to the ubuntu partition, it has suggestions for installing it if you are currently using Grub (Old version) and hence had access to ubuntu.

---

### Post by zvacet on 2010-03-08
> I have done a fresh install of karmic, so I am assuming that would of installed grub2 with it?

It should install it.If you have choice witch OS to boot then grub is installed.


> There seems little on the page about install Grub2 from the live CD for an installed system when you can't get access to the ubuntu partition

You will get access by mounting partition.

> SIMPLEST - Copy GRUB 2 Files from the LiveCD

This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods. 
Boot to the LiveCD Desktop (Ubuntu 9.10 or later). 

Open a terminal by selecting Applications, Accessories, Terminal from the menu bar. 

Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L". 
sudo fdisk -l
If the user isn't sure of the partition, look for one of the appropriate size or formatting. 

Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently. 
[B]Mount the partition containing the Ubuntu installation. 
sudo mount /dev/sd''xY'' /mnt[/B]

Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot 

Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device. 
sudo grub-install --root-directory=/mnt/ /dev/sdX

Example: sudo grub-install --root-directory=/mnt/ /dev/sda 
Reboot 

Refresh the GRUB 2 menu with sudo update-grub

---

### Post by presence1960 on 2010-03-08
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

