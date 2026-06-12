---
title: "Installation saving one partition..."
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by FrankGun on 2013-04-07
Hello guys,

Pls, I have a problem. After another crash of my XP, I decided to install Ubuntu (or Mint).
Pls, see attached, I have this kind of partition. 

dev/sda1 is my old C: where XP is installed.
dev/sda2 is my Slave where I have my data, and **I don t want to remove**.
unallocated is a mistery, I don t know what is it. maybe something from my old installation of Linux

So, pls, can u tell me what I can do? I want to install Ubuntu or Mint (I think it s the same) but I want to keep my sda2.
So, I know I have to create other partitions, can u instruct me?
Many thanks.

Francesco

---

### Post by oldfred on 2013-04-07
You really should have a good backup of your data. Any repartitioning has the potential to cause data loss, especially if you have a power failure or interrupt the process in the middle of writing data.

Are you planning on totally erasing Windows? Many come back later as they have one application or game they cannot live without that only runs in Windows. Most general computer use things work well in Linux but it is not Windows. 

Your sda2 is an extended partition filled with one logical partition sda5. The unallocated is just a small amount of space at the end of the drive. I would not worry about it.
NTFS partitions need 30% free space to work well, when down to 10% they slow to a crawl and that is many times why users complain about slow Windows.

If totally overwriting Windows you have to reformat sda1 to a Linux format, usually ext4 and you can just install to that partition. But you have to use manual install, as the choice to install to entire drive is the entire hard drive including all your data,  not just partition sda1 or what Windows calls the c: drive.

While most of these are dual boot, you can use the same process, just the Something Else or manual install option. If you just erase sda1 and leave it unallocated you will get another install option, install into the unallocated space. That should not overwrite your existing install either. But I prefer to use manual install so I know exactly what system is doing, but you do have to understand partitions, formats and mount points like / (root) and swap.

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by FrankGun on 2013-04-07
Hi !
thanks for your support. my situation is:
my Xp is crashed, so I have to format my sda1 and put Ubuntu in.
Maybe in the future I will install also an XP, so I d like to divide my sda1 into 2 partitions, one with ext2 for Ubuntu, the other one in NTFS for Xp.
Now, what are the spaces I have to allocate for them? I can also take some space from sda5 (date).
So, manually I have to create also SWAP sda, I have 2GB Ram, I have to allocate 4Gb for Swap?
thanks

---

### Post by oldfred on 2013-04-07
You do not have a lot of room.
While you can install either XP or Ubuntu in much less than suggested, you usually cannot do much. I have seen XP should be 20GB and normally suggest Ubuntu as 10GB as minimum. You can install Ubuntu in 5.4GB, and Lubuntu in less, but then you do not have room for updates or added software, much less your data.

Your data partition, sda5 uses 60GB, so I would not make it smaller than 75GB. You then could fit Ubuntu in 10-15GB with 2.2GB of swap. You need swap equal to RAM in GiB. Only if RAM was less than 1GB would you need double RAM size.
So maybe shrink sda5 to 75GB and install Ubuntu in sda6 formatted ext4 and swap of 2.2GB? The you still have sda1 for XP. Windows has to be installed in a primary so you never could install it in the extended partition as a logical and it prefers to be first so leaving sda1 for a reinstall of Windows is probably best.

---

