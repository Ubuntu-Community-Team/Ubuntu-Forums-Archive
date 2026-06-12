---
title: "second disk as data"
date: 2018-09-25
forum: Installation &amp; Upgrades
---

### Post by thaddeus2 on 2018-09-25
Hi, 


My environment is as under 

HDD 1 : 100 GB SDA
HDD 2 : 100 GB SDB 

 Physical

I need SDA to have the OS, Mount, Boot partitions
I need SDB to be defined as ext4 and only used for data

I want to achieve all this via GUI.

Please let me know how to get this partition 

The HDD2 i.e. SDB will be only used for data storage as I need OS on seperate disk and data on another.

---

### Post by yancek on 2018-09-25
If you have your OS on sda, just boot it with the second drive attached, create partitions on the second drive and format it/them using GParted.  The GParted manual is at the link below and explains everything in detail.

 [https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by thaddeus2 on 2018-09-25
Hi thanks for the input. 

I dont want to use gparted. 
during installation i get a gui where i can choose the partition and format. 

I just need to know the proper option so that i can get the sdb as data disk and set it up.

---

### Post by oldfred on 2018-09-25
You end up having to use gparted.
You can use installer for all the system partitions, essentially now just / if BIOS or ESP & / if UEFI.
But installer does not have creation of a data only partition.
You can during install put /home on sdb which has all your data, but also your user configuration files, most in hidden (leading . files) that are not large.

I primarily use a separate data partition as I mount it in multiple Ubuntu installs, but do not want /home as that is usually different settings in each test install. I also want my /home inside / on SSD but data on HDD does not have to be on as fast of a drive.

As a newer user the separate /home may be the easiest way to configure system.

---

### Post by thaddeus2 on 2018-09-25
hi,

what if i keep sdb without any partitioning for now and then download gparted and through gparted configure sdb wil that be okay?

---

### Post by ajgreeny on 2018-09-25
The live OS you use to install your Ubuntu system has **gparted** available on it by default so there is no need to download anything else and there is no reason to fear its use, as you seem to.

Put your OS on sda1 in the usual way, then still in the live OS open gparted and create an ext4 partition on sdb1, label it DATA if you wish, though that is not really necessary but it does help when trying to remember which partition is which, particularly if you have many partitions to sort out.

Once the OS is installed and running you will find that you can not write to sdb1 as a normal user as it will be owned by root; to enable you as user to write to it you need to change the owner with command  ```
sudo chown -R username:username mountpoint
``` 
You will need to set the mountpoint of sdb1 in /etc/fstab in order to mount it at boot time with a line such as > UUID=*xxxxxxxxxxxxxxxx* /mnt/data ext4 defaults,  0 1 and you will find the UUID with ```
sudo blkid
```
You will also need to create that mountpoint with ```
sudo mkdir /mnt/data
```

As you see from this, it may be easiest to simply create a separate /home partition on sdb at install time, as suggested by oldred in post #4

---

### Post by westie457 on 2018-09-25
If you use the 'something else' option to install you can create the partition and in the 'mount point' box type in /Data an entry is created in fstab.

---

### Post by thaddeus2 on 2018-09-25
> **westie457 said:**
> If you use the 'something else' option to install you can create the partition and in the 'mount point' box type in /Data an entry is created in fstab.

Thanks for the valuable inputs. 
I'm new to linux hence need to be sure what i'm doing. 

I will select something else and for sda ill put the /home /swap partitions 

For sdb i will lablel as /data ext4 and full size. Will this automatically do all the fstab entries for me after reboot and i dont have to mount anything via cli?

Please help.

---

### Post by westie457 on 2018-09-25
> [COLOR=#000000]Will this automatically do all the fstab entries for me after reboot and i dont have to mount anything via cli?
It should work for you and you will have full permissions associated with your account.
[/COLOR]

---

### Post by westie457 on 2018-09-25
Hold up, have just checked the machine for details.

Most of my earlier post in the 'something else' option was correct apart from choosing the Mount point.
In the Mount Point box type in /home/'your user name/Data instead of just '/Data'.
It took me a couple of tries to get it right for the permissions.

---

