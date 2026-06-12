---
title: "How much for each partition ?"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by anjanesh on 2008-06-17
Hi

Im finally getting to install Ubuntu 8.04 64-bit (after a series of failed installations due to corrupted downloads )

I got a 500GB SATA hard-disk and 8GB DDR2 RAM - all of which is dedicated to linux !
So what should I give for partitions ? (Use: web-development, graphics)

200GB for **/**
5GB for **swap**
100GB for **/home**
195GB **free**

?

I later would like to install Fedora Core 9 - dual boot.
What will happen during FC9 setup on partitioning ? Will it need a separate **/**, **/home** etc ?

Thanks

---

### Post by raedbenz on 2008-06-17
HI,
swap size according to Ubuntu documentations should be twice the RAM size.
the root directory "/" i personally see that is too much 200Gb.all what u need for Ubuntu is only 8 GB.
home directory is the place where u will have all your work saved.So the larger the better
cheers

---

### Post by anjanesh on 2008-06-17
>  the root directory "/" i personally see that is too much 200Gb.all what u need for Ubuntu is only 8 GB. I thought thats only when using the bare minimum.

What happens when you install a whole lot of other packages like Open Office, web servers, databases ?

Where do these goto ?

---

### Post by wpshooter on 2008-06-17
I would make / root about 20 to 25gb to give you some room for growth.

Would put about 1gb in SWAP, since you are probably not likely to need it.

Would put the balance in /home or elsewhere for storage, etc.

---

### Post by anjanesh on 2008-06-17
> I would make / root about 20 to 25gb to give you some room for growth. Where do new installations go anyway ?

>  Would put the balance in /home or elsewhere for storage, etc.I have set 100GB for /home.
Unlike Windows where we can have a blank D:, E:, how do I setup free storage in Linux without mounting it ?

---

### Post by meindian523 on 2008-06-17
Whatever you install goes to /,but openOffice comes installed with the default installation,about 15-20 GB max is enough for /,1 GB swap,rest /home.New installs will need their own / partitions,so they won't take up space on your Ubuntu /.If you have partitions which are empty but you don't want mounted automatically,just remove auto from the lines of those partitions in /etc/fstab,or if "auto" does not exist,place a > # in front of those lines.Or don't create partitions on them at all.

---

### Post by anjanesh on 2008-06-17
What about mounting /var, /local etc ? Does it do any good ?

In Windows, I keep C: to 50GB for OS & Program Files.
I have D: of 100GB and E: 150GB for storage.

The problem during linux installation is that I got to set a mount point for every partition (unless its swap etc). 

How can just reserve 300GB of my hard-disk space as blank ?

---

### Post by meindian523 on 2008-06-17
mounting /var etc won't be much use if you are using it as a desktop system.Really,you have a problem of plenty.Just don't create any partitions for the 300 GB [or] make a few mountpoints yourself like maybe /media/<whatever you want>,you can type that into the mount point box in the partitioning program.

---

### Post by anjanesh on 2008-06-17
Wow ! I didnt realize we could create out own mount points.
So basically, just like in Windows, when I created a 150GB partition for my data and labeled the volume data, I can do the same for Linux by naming it /data ?

> Just don't create any partitions for the 300 GB If dont create a partition at all then it said it would be unusable - during installation.

---

### Post by meindian523 on 2008-06-17
yup,but it's preferable to use /media/data and obviously non-partitioned space will be unusable coz it will be without a filesystem.But then you don't have to see anything whether it should automatically mount or not.And you can create a partition whenever you wish.

---

### Post by wraezor on 2008-06-17
500MB for /boot

Set up the rest in LVM, then you can expand as needed.

Start out with:
20GB for /
1GB for swap
100GB for /home

---

### Post by anjanesh on 2008-06-17
Half a GB for **/boot** ? Does it just contain the bootloader ?

But if I want to install ubuntustudio or NetBeans then where does it go to ? **/** right ?
So if I run out of **/** space later how would I expand 20GB to 50GB - I understand that process in partition manager is very lengthy and heavy.

---

### Post by meindian523 on 2008-06-18
/boot needs only about 150 MB.And it contains only the bootloader.If you install UbuntuStudio as a package,it will go to /.If you install it as a distro,it will need it's own /.You can leave out some unallocated space at the end of your / partition,so that you can just extend your partition using GParted without affecting your other partitions.

---

### Post by anjanesh on 2008-06-18
Considering that I'll probably use Ubuntu in future for a lot of other applications (after migrating from Windows), I'll probably allot in this order :

250MB for **/boot**
50GB for **/**
300GB for /home
5GB for swap

so that later I can install FC9 on a separate partition-drive and FC9's partitions
250MB **/boot**
50GB  **/**
5GB swap

remaining ~90GB for free-space or FAT32 shared drive or something.

But my question is - Can **/home** created by Ubuntu be shared by FC9 ?

---

### Post by meindian523 on 2008-06-18
You don't NEED 250MB for /boot.My 150 MB /boot has only used 41.8 MB.You can share your /home but I'm unsure whether you can use the same username.

---

### Post by bkline on 2008-06-18
> **anjanesh said:**
> But my question is - Can **/home** created by Ubuntu be shared by FC9 ?

Yes it can.  The only potential problem is that software packages that store settings in subdirectories under the home directories might get confused, particularly if the packages are at different versions (as they almost certainly will be in some cases).  A way around this problem, if the system is not going to be used by multiple users, is to create a mount point for a directory like **/home/anjanesh/data** which you mount to a common partition shared by the two distros, and just discipline yourself to put all your own data files there.

---

