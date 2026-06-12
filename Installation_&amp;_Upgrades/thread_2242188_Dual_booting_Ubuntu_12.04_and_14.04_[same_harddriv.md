---
title: "Dual booting Ubuntu 12.04 and 14.04 [same harddrive]"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by gowtham-pro on 2014-08-31
I want to install Ubuntu 12.04 and 14.04 on the same drive. I have already installed Ubuntu 12.04 and I have manually partitioned the drive. 


  300 MB boot; 20 GB root; 400 GB Home; 5GB Swap


  500 GB is unpartitoned. (left for 14.04)


  Now I want to install 14.04. How do i go about partitioning the remaining 500 GB for 14.04. I will create another Home and root partition, but do I also have to  create another boot partition? I don't want to have any grub issues. I  just want both the installation to be separate and neat.

---

### Post by grahammechanical on 2014-08-31
Me? I do not use a boot partition. I have one large partition where I keep my data. I also have several 25 GB partitions where I install different versions and flavours of Ubuntu. Each install creates a /boot folder and a /home folder in the partition. I can access my data partition whatever version of Ubuntu I am working from. And if I need to re-install, then my data is safe.

Your way, would indeed require separate / (root); /boot; /home partitions. The Something Else option of the installer will allow you to set up those partitions and the new install will work just find. There will be no confusion as to which partition is being use by which OS. The partitions are given a unique identification code.

But I would not use the same partition for /home for two installations. It can be done but there will be a mixing of folders and user configuration files.

Regards.

---

### Post by gowtham-pro on 2014-08-31
> **grahammechanical said:**
> Me? I do not use a boot partition. I have one large partition where I keep my data. I also have several 25 GB partitions where I install different versions and flavours of Ubuntu. Each install creates a /boot folder and a /home folder in the partition. I can access my data partition whatever version of Ubuntu I am working from. And if I need to re-install, then my data is safe.

Your way, would indeed require separate / (root); /boot; /home partitions. The Something Else option of the installer will allow you to set up those partitions and the new install will work just find. There will be no confusion as to which partition is being use by which OS. The partitions are given a unique identification code.

But I would not use the same partition for /home for two installations. It can be done but there will be a mixing of folders and user configuration files.

Regards.

Thanks for the reply. 

I'm just experimenting things. I think your method is more efficient and easy to access all the data from any installation. So this is what I understand. If I have 1TB storage, I can use 500 GB for Data and allocate a separate Swap partition for all the OSs to use and create small 50GB partitions for each and every OS I wish to install. In each and every small 50 GB partitions will have root, home, and boot for that particular OS. This wouldn't break Grub right? Appreciate your help.

---

### Post by Dennis N on 2014-08-31
> **gowtham-pro said:**
> Thanks for the reply. 

I'm just experimenting things. I think your method is more efficient and easy to access all the data from any installation. So this is what I understand. If I have 1TB storage, I can use 500 GB for Data and allocate a separate Swap partition for all the OSs to use and create small 50GB partitions for each and every OS I wish to install. In each and every small 50 GB partitions will have root, home, and boot for that particular OS. This wouldn't break Grub right? Appreciate your help.

What is going to happen when you install grub to the MBR each time is that the grub from the most recent install is the one that is working in the end. So you need to know that. So, if you had a nice custom grub menu set up you will lose it when you install a second OS unless you take special steps to prevent its grub from taking over.

I don't use separate home partitions in the installations, but a separate data partition like grahammechanical does. I also do not use boot partitions. 

All this assumes these are not being installed in UEFI mode on a GPT disk. Then you may have a problem getting two Ubuntus on there.

---

### Post by gowtham-pro on 2014-08-31
> **Dennis N said:**
> What is going to happen when you install grub to the MBR each time is that the grub from the most recent install is the one that is working in the end. So you need to know that. So, if you had a nice custom grub menu set up you will lose it when you install a second OS unless you take special steps to prevent its grub from taking over.

I don't use separate home partitions in the installations, but a separate data partition like grahammechanical does. I also do not use boot partitions. 

All this assumes these are not being installed in UEFI mode on a GPT disk. Then you may have a problem getting two Ubuntus on there.

Then how do I go about achieving this? All I want is to install 2 Ubuntu installations. Or lets keep things simple. How about this?

ext4 - Ubuntu 14.04
ext4 - Ubuntu 12.04
Swap 

I just don't want to deal with any grub issues. 

Thanks

---

### Post by Bashing-om on 2014-09-01
gowtham-prol Hi ! 

Like many I too multi-boot on multiple hard drives .
```

##My primary OS##
sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  1.8G  2.8G  39% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  744K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   20M  2.0G   1% /run/shm
none            100M   16K  100M   1% /run/user
/dev/sda2       9.5G  1.3G  7.8G  14% /home
/dev/sda8       4.7G  1.6G  2.9G  36% /var
sysop@1404mini:~$ 

##All my disks/partitions##
sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1                    63   976768064   488384001   83  Linux
sysop@1404mini:~$
##and how I am doing it##
sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$

```
Dual booting 'sda' and 'sdc' with grub installed to MBR on each.
Once you learn how, managing grub - and fixing it when it breaks - is no big deal .

[INDENT][INDENT]just food for thought
[INDENT][INDENT][INDENT]for what works
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-09-01
It is much simpler to just create one partition for the filesystem, maybe a swap and then create a separate partition for data.  You can then put whatever data you have such as documents, pictures, videos or what ever on this partition and have it mounted and accessible from either operating system, in your case 12.04 and 14.04.  Since both systems will be on the same drive, install Grub from the new 14.04 to the master boot record as part of the installation and it will detect 12.04 and create an entry for it in the boot menu.

I have both systems installed as well as about 10 other operating systems and find this a much simpler method.

---

### Post by Dennis N on 2014-09-01
> **gowtham-pro said:**
> Then how do I go about achieving this? All I want is to install 2 Ubuntu installations. Or lets keep things simple. How about this?

ext4 - Ubuntu 14.04
ext4 - Ubuntu 12.04
Swap 

I just don't want to deal with any grub issues. 

Thanks

That is really all you need. A root partition for each OS, and a swap partition that either will use. Whichever you install second will control the grub, but it is probably not going to make any difference to you which that is - either will pick up the other and list it in the grub menu*. If you are undecided about the data partition idea, you can easily create one later out of unallocated space. As it is, either OS can access files in the other one.

* possibly better to do 14.04 last, as it MAY give a cleaner grub menu.

If this is an MSDos Partition table, and the ones you show are primary partitions, remember the next partition should be an extended partition using the rest of the disk (to be then carved up into logical partitions). A data partition would be one if these. 

Possible Partitions:
> sda1 Ubuntu 12.04
sda2 Ubuntu 14.04
sda3 swap
sda4 Extended (using remaining disk space)
--sda5 (logical) Data 
--unallocated in sda4


I would leave unallocated space for future expansion. Once you see how easy this is, you may want to add additional OS installs, for example. Good luck.

---

### Post by yancek on 2014-09-01
I think it is a lot simpler to create just one partition for the entire filesystem of each distribution you install.  15-25GB should be more than enough but if you have a large drive or multiple drives, you can make the partitions larger.  Then create an Extended partition as suggested above and you can create various partitions for different types of data.

---

