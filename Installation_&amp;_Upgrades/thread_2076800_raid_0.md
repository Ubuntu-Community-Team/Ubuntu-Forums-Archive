---
title: "raid 0 ?"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by hiperflash on 2012-10-27
hey, 

i just wanted to ask is it safe to install new MD after installing ubunto server? (i mean is it safe to insert installation disk again and modify MD after fresh installation) i did something bad with MD in the middle of the installation and i have only 3.8gb fre space and not 1TB+/-.. 

my system is ubunto server 12.04.

system is actually detecting disks but i cant use them. i tried to fix it over vnc but i dont have "permissions" even if i log with root and when i try to run GPart prog i type root password and GPpart wont start :(

help?

ty greetz ;)

---

### Post by darkod on 2012-10-27
First, why VNC and not ssh? Also, since you mention VNC and Gparted which are usually GUI tools, did you add a GUI on your ubuntu server installation? Or this is a desktop OS used as a server?

Yes, usually you could add a MD even without booting with the cd again. You use the cd to install, if you already have the OS installed you can simply add a new MD if that's what you want to do.

On the other hand, if you want this new MD to be the root partition and you don't have too much customization done on the machine since the original install, it might be better to simply do a new installation. It would be a little complicated to switch the root partition.

If the MD is planned for data, you can easily do it.

Enter your server with ssh and post the output of:
sudo parted -l (small L)

---

### Post by hiperflash on 2012-10-27
> **darkod said:**
> First, why VNC and not ssh? Also, since you mention VNC and Gparted which are usually GUI tools, did you add a GUI on your ubuntu server installation? Or this is a desktop OS used as a server?

Yes, usually you could add a MD even without booting with the cd again. You use the cd to install, if you already have the OS installed you can simply add a new MD if that's what you want to do.

On the other hand, if you want this new MD to be the root partition and you don't have too much customization done on the machine since the original install, it might be better to simply do a new installation. It would be a little complicated to switch the root partition.

If the MD is planned for data, you can easily do it.

Enter your server with ssh and post the output of:
sudo parted -l (small L)

yes i added part gui.. so that the problem i guess? 
and this is server edition for server. and im using putty :) 

you mean that i can install ne md from terminal or when i boot from cd and in the midle of instalation?

oh well i done some things there that why i dont wanna do it again. 

is there any good tutorial how to set up perfect raid with 3 disk?

ty greetz

---

### Post by darkod on 2012-10-27
The mdadm package is included in the server version. Yes, I am talking about using putty (ssh) and configuring the mdadm raid you want.

Are you going to use three new disks for it, or you are already using the disks right now? That's why I asked for the parted info, it can explain some thing better (if you already have the disks connected).

---

### Post by hiperflash on 2012-10-27
> **darkod said:**
> The mdadm package is included in the server version. Yes, I am talking about using putty (ssh) and configuring the mdadm raid you want.

Are you going to use three new disks for it, or you are already using the disks right now? That's why I asked for the parted info, it can explain some thing better (if you already have the disks connected).

```
Model: ATA ST3320620NS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      1048kB  1072MB  1071MB  extended
 5      1049kB  1072MB  1071MB  logical                raid
 1      1072MB  320GB   319GB   primary                raid


Model: ATA ST3320620NS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      1048kB  1073MB  1072MB  extended
 5      1049kB  1073MB  1072MB  logical                raid
 1      1073MB  320GB   319GB   primary                raid


Model: ATA ST3320620NS (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 2      1048kB  1073MB  1072MB  extended
 5      1049kB  1073MB  1072MB  logical                raid
 1      1073MB  320GB   319GB   primary                boot, raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 957GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  957GB  957GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md1: 3212MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  3212MB  3212MB  ext4
```

here you go :) i hope that will help to explain some things :)
and as i said i screwed setting up MD settings.. :(

---

### Post by darkod on 2012-10-27
OK. Now give us some more info what do you actually want to do.

It seems you have two raid0 devices, md0 and md1. md1 is very small, about 3GB, and md0 is 957GB.

Do you have any data on these devices, or you can destroy them and create raid5?

---

### Post by hiperflash on 2012-10-27
> **darkod said:**
> OK. Now give us some more info what do you actually want to do.

It seems you have two raid0 devices, md0 and md1. md1 is very small, about 3GB, and md0 is 957GB.

Do you have any data on these devices, or you can destroy them and create raid5?

yea well all files are on that md1 disk witch is root.. 
well i wanna merge those disks to that root one. so i can actually have 1TB..

---

### Post by darkod on 2012-10-27
Well, moving the root partition can sometimes be complicated, but it's doable. However, there are two main questions:
1. Do you also want to change the raid level to raid5? Judging by the MD devices sizes, you are running raid0 right now which splits the data between the three disks. Raid0 doesn't give you any redundancy and if one disk dies you lose all the data.
If you want to switch to raid5 which can keep working if one disk dies, you would have to reinstall from scratch.

2. How easy or complicated is it to reinstall from scratch? Do you have lots of customization that you would need to repeat in the new installation? If the system is more or less the default, I think it's best to reinstall again regardless whether you want to move to raid5 or keep going on raid0.

---

### Post by hiperflash on 2012-10-27
> **darkod said:**
> Well, moving the root partition can sometimes be complicated, but it's doable. However, there are two main questions:
1. Do you also want to change the raid level to raid5? Judging by the MD devices sizes, you are running raid0 right now which splits the data between the three disks. Raid0 doesn't give you any redundancy and if one disk dies you lose all the data.
If you want to switch to raid5 which can keep working if one disk dies, you would have to reinstall from scratch.

2. How easy or complicated is it to reinstall from scratch? Do you have lots of customization that you would need to repeat in the new installation? If the system is more or less the default, I think it's best to reinstall again regardless whether you want to move to raid5 or keep going on raid0.

i guess go for new install :/ 
can you give me some good tutorial for raid 5 set up? btw im not at home but what if i dont have raid 5?

---

### Post by darkod on 2012-10-27
If you go for a new install, it's your choice whether you go with raid0 and raid5. You can find more information about different raid levels here and on many other websites:
[http://en.wikipedia.org/wiki/Raid_levels](http://en.wikipedia.org/wiki/Raid_levels)

I don't have any specific tutorial at hand but using raid during the ubuntu server installation is quite easy.
Just create equal partitions on all disks for all the different MD devices you plan to use (root, swap, /home, etc) and when selecting those partitions one by one in the Use As field select Physical device for RAID. That will mark it as raid partition.

When you are done creating all partitions, in the partitioner screen go to Configure Software RAID at the top. In there you create the devices (/dev/md0, /dev/md1, etc) and you choose which level to use, number of devices, and which devices. When selecting which devices be careful to select the correct ones, and you make the selection using the Space bar. You will see the * sign to confirm the selected partitions.

After you create the MD devices and go back to the partitioner screen, they will show up there. Select them one by one and for each select the correct Use As (ext4 or swap), and the correct mount point (like /, /home, etc). Swap doesn't use mount point so don't get confused by that.

And that's it.

---

