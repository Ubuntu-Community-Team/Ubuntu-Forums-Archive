---
title: "Set correct partitions and mountpoints during install"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by p8r on 2013-01-15
Hi there,

I just bought recently a new HDD and I'd like to install Ubuntu 12.04 64bit on it as OS. Since I'm a bit new to Linux I don't know exatly how should I create the partitions to fit my needs. I'd like to have 4 partitions in the following order:
1. SWAP (6GB as my RAM)
2. System (30 GB, mounted to /)
3. Home (400 GB, mounted to /home)
4. www (50 GB)

I'm developing websites so I'd like to have a separated partition just for these projects (www). Where should I mount it? Can I mount it also to / or should I mount it to /var/www ?

---

### Post by darkod on 2013-01-15
The choise where to mount it is yours. You can mount it directly at /var/www or you can make some data mount point like simply /data. However, if you want apache to read the files directly from /data you will have to do some changes in the configuration I guess (I haven't worked much with apache).

---

### Post by p8r on 2013-01-16
> **darkod said:**
> The choise where to mount it is yours. You can mount it directly at /var/www or you can make some data mount point like simply /data. However, if you want apache to read the files directly from /data you will have to do some changes in the configuration I guess (I haven't worked much with apache).
Thanks for the reply Darkod, it's good to know that I have this kind of freedom. Ubuntu rocks.:)

---

### Post by SeijiSensei on 2013-01-16
When you reach the disk partitioning stage during installation, pick "manual."  You can then specify the sizes, filesystems, and mount points for each partition.

I strongly recommend you don't use four primary partitions.  I'd make swap and maybe / be primaries, but make the rest an extended partition. Then you're not limited to four partitions and can make changes more easily if you need to.

I sometimes create the partitions before installation by running off the installation medium in "Try Ubuntu" mode and using [fdisk]("http://www.tldp.org/HOWTO/Partition/fdisk_partitioning.html") from the command line to create the partitions.

---

### Post by p8r on 2013-01-16
> **SeijiSensei said:**
> When you reach the disk partitioning stage during installation, pick "manual."  You can then specify the sizes, filesystems, and mount points for each partition.

I strongly recommend you don't use four primary partitions.  I'd make swap and maybe / be primaries, but make the rest an extended partition. Then you're not limited to four partitions and can make changes more easily if you need to.

I sometimes create the partitions before installation by running off the installation medium in "Try Ubuntu" mode and using [fdisk]("http://www.tldp.org/HOWTO/Partition/fdisk_partitioning.html") from the command line to create the partitions.
Thank you for these infos. And just one more question. What kind of filesystem should I use? Ext2, Ext3, Ext4?

---

### Post by darkod on 2013-01-16
I use ext4, not sure if someone else will have preference for the older ext3/ext2.

---

### Post by p8r on 2013-01-17
> **darkod said:**
> I use ext4, not sure if someone else will have preference for the older ext3/ext2.
Ok, thank you. Since then I googled about these types, and now I see what's the difference. But for me it was a bit new thing. 

Now I'm facing with an other problem, but this will be an other thread. :) 

Learning something new is always funny. :)

---

