---
title: "Need help partitioning"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by Extol11 on 2013-02-01
So my laptop's hard drive failed two days ago and I bought a new one. Since I no longer have to worry about keeping the partitions that Asus put on it and the copy of the Windows 7 OS in its backup partition I decided to learn how to partition a hard drive and install Ubuntu side-by-side with Windows 7. So I made three partitions on a 500GB hard drive. One of them is 150GB, another one is 20GB and the last one for data is all of the remaining space. I formatted the 20GBs one with Ext 3 to ready it for Lubuntu ( I chose 20GB because I'm only going to use it for simple image editing and a lamp server to practice, btw. after checking my current Lubuntu installation I found out I have only used 5GB on it). So I boot up Lubuntu 12.10 on the laptop, tell it to install on the 20GB ext3 partition and it tells me I have to define other stuff like the swap partition and other stuff I'm still researching. I thought the OS would take care of that by itself. 

So can anyone tell me where I can find a good tutorial or if there's a way for Lubuntu to do this for me? This is the first time I ever install two OS in the same hard drive since I favor a separate hard drive for each OS. 

BTW, I used gparted for partitioning and Windows 7 is already installed and working fine.

---

### Post by Thee on 2013-02-02
If you didn't already partitioned your hard drive, then you could have selected to install Ubuntu along side with Windows and the installation would take care of the rest.

But since you already created ext partition, go ahead and make another one to be used as swap space. It's usually suppose to be twice the size of your RAM. So if you have for example 2GB ram, make 4GB swap partition.

Then you wont have any problems during the installation.

Note that you might need to shrink the "Data" partition that you created in order to make room for one more partition (swap).

---

### Post by Topsiho on 2013-02-02
There are 3 kinds of partitions, which you should be aware of when creating partitions on a hard disk:

1) primary partitions. You can create no more than 4 primary partitions on a disk.
2) If you need more partitions, then you should sacrifice at least one of the primary partitions and create an extended partition in it's place. In this you can create
3) one or more logical partitions. I don't know how many are allowed, but certainly more than you'll need. Of course there should be enough room for them in the extended partition.

Topsiho

---

### Post by ibjsb4 on 2013-02-02
Good stuff  :)

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by presence1960 on 2013-02-02
I would make the 20 GB partition an extended partition. Then create a swap partition and an ext 3 or ext 4 logical partition inside the extended partition. You can do this with gparted. When you install Ubuntu don't choose side by side or Entire disk, choose Something Else. When your disk layout appears highlight the partition for Ubuntu and click "Change". Set the mount point as " / " and choose your file system (ext 3 or ext 4) Then proceed with the installation.

BTW depending on the amount of RAM you have you may get away with no swap. I always create a swap equal to my RAM which is necessary if you want to use hibernate function. 12-15 GB is plenty for most users / (ubuntu partition).

---

### Post by Extol11 on 2013-02-02
Thanks for all of the info. I'm reading it and considering options. I think I'll just delete that ext3 partition and let Ubuntu handle everything. But if I manage to learn how to do this myself, I'll have an advantage next time I want to do this kind of stuff.

---

### Post by presence1960 on 2013-02-02
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/GraphicalInstall#Installation_type](https://help.ubuntu.com/community/GraphicalInstall#Installation_type)

---

### Post by ibjsb4 on 2013-02-02
In that case don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Extol11 on 2013-02-02
> **Thee said:**
> If you didn't already partitioned your hard drive, then you could have selected to install Ubuntu along side with Windows and the installation would take care of the rest.

But since you already created ext partition, go ahead and make another one to be used as swap space. It's usually suppose to be twice the size of your RAM. So if you have for example 2GB ram, make 4GB swap partition.

Then you wont have any problems during the installation.

Note that you might need to shrink the "Data" partition that you created in order to make room for one more partition (swap).
I read in a tutorial that it did not have to be twice the size of the ram and that there was a whole lot of debate on how much size to put on it. I have 4 gigs and I don't feel like giving the swap partition 8 gigs out of the 20gigs really. I'm considering deleting the partition and letting Ubuntu deal with it.

---

### Post by presence1960 on 2013-02-02
> **Extol11 said:**
> I read in a tutorial that it did not have to be twice the size of the ram and that there was a whole lot of debate on how much size to put on it. I have 4 gigs and I don't feel like giving the swap partition 8 gigs out of the 20gigs really. I'm considering deleting the partition and letting Ubuntu deal with it.

The most you will need is equal to your RAM if you want to use the hibernate function. With 4 GB of RAM you can do without a swap, but you won't be able to hibernate.

---

### Post by Topsiho on 2013-02-02
If you have 4 GB of RAM then probably your swap partition will not be used. It might however, and I don't know what will happen if it is not there, when needed. But I feel the two times RAM rule is a little excessive here.

Topsiho

---

### Post by presence1960 on 2013-02-02
> **Extol11 said:**
>  I'm considering deleting the partition and letting Ubuntu deal with it.

> So my laptop's hard drive failed two days ago and I bought a new one. Since I no longer have to worry about keeping the partitions that Asus put on it and the copy of the Windows 7 OS in its backup partition I decided to learn how to partition a hard drive and install Ubuntu

Don't let ubuntu take care of it. Make the 20 GB partition an extended partition. Inside the extended partition create a 4GB swap partition and logical 16 GB ext 3 or ext 4 partition for ubuntu. Then follow my earlier instructions to install.

You said you wanted to learn, now here is your opportunity.

---

### Post by presence1960 on 2013-02-02
> **Topsiho said:**
> If you have 4 GB of RAM then probably your swap partition will not be used. It might however, and I don't know what will happen if it is not there, when needed. But I feel the two times RAM rule is a little excessive here.

Topsiho

Definitely excessive. With 4 GB of RAM the swap would most likely seldomly be utilized. The most utilization will occur if you hibernate. What will happen all your open processes which are already in RAM anyway will be transferred to swap so computer can hibernate. When you awaken it the info will be tranfered from swap on the hard disk back into RAM. That is where the max swap equal to your RAM comes from.

---

### Post by Extol11 on 2013-02-02
> **presence1960 said:**
> Don't let ubuntu take care of it. Make the 20 GB partition an extended partition. Inside the extended partition create a 4GB swap partition and logical 16 GB ext 3 or ext 4 partition for ubuntu. Then follow my earlier instructions to install.

You said you wanted to learn, now here is your opportunity.

OK. I already told Gparted to delete that partition. I'll redo it and do what you suggested. Anything else I might want to know?  Also, gparted just told me that moving partitions might mess the OS and not let it boot. I don't have any problems with reinstalling windows but what should I leave alone so that this doesn't happen? And thanks for all of the help, man. It's greatly appreciated.

edit: Nvm, I found out Ubuntu uses ext4.

---

### Post by presence1960 on 2013-02-02
> **Extol11 said:**
> OK. I already told Gparted to delete that partition. I'll redo it and do what you suggested. Anything else I might want to know?  Also, gparted just told me that moving partitions might mess the OS and not let it boot. I don't have any problems with reinstalling windows but what should I leave alone so that this doesn't happen? And thanks for all of the help, man. It's greatly appreciated.

edit: Nvm, I found out Ubuntu uses ext4.

Don't move partitions. Where the 20 Gb partition is, just delete that one. Then make a new extended partition 20 GB in size from the unallocated space. Then make the 4 GB swap and 16 GB ext 4 logical partition within the extended partition. Sorry for the delay, was playing checkers with my daughter.

Edit: when you install choose Something Else. When your partition table (layout) appears highlight the 16 GB ext 4 partition, click change. Set mount point to " / ". Choose ext 4 as file system and proceed with the install. Windows should remain intact.

---

### Post by Thee on 2013-02-02
> **Extol11 said:**
> I read in a tutorial that it did not have to be twice the size of the ram and that there was a whole lot of debate on how much size to put on it. I have 4 gigs and I don't feel like giving the swap partition 8 gigs out of the 20gigs really. I'm considering deleting the partition and letting Ubuntu deal with it.

Well sorry then for the misinformation, I remember that was the general rule about 10 years ago when I first wanted to try Linux :)

---

### Post by Extol11 on 2013-02-02
> **Thee said:**
> Well sorry then for the misinformation, I remember that was the general rule about 10 years ago when I first wanted to try Linux :)
No problem. I read the same thing in a manual when I was installing Debian "woody" for a class around 2005. It was the first time I was messing with linux at all and I'm glad to find out that that's not necessary anymore. I did not want to imagine what I would have to do once I got my desktop up to 32GB of ram as planned. LOL

PS: I'm marking this as solved. Thanks to everyone who helped.

---

