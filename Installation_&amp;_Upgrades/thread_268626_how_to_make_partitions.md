---
title: "how to make partitions"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by cmaranhao on 2006-09-30
hi, i already used linux (a friend of mine made the installation for me), but i formated the pc and now i regret it big time.. and i don't have my friend to instal it this time for me!

so, i am trying to instal linux by myself but i am having some problems with the partitioning.. my version of linux is Ubuntu 6.06 LTS

ok, onto business, i hope you guys can help me..

i have 3 hard drives...one with 17Gb, other with 80Gb and another with 200Gb.

>i want to split the 80Gb in three partitions so:

in the first partition, 12Gb will be enough, i want to instal linux.
in the second partition, 12Gb will be enough, i want to instal windows XP so that i can have dualboot (i need to work with a certain program that only runs in windows!)
in the third partition, i want to have it for saving files.

>in the 17Gb hard drive i want to spit in two.. one partition for swap, the other for amule..so, will 1024mb be enough for swap?

>i don't want to mess up with the 200Gb hard drive, i have data there that i don't want to loose. like i said, i already used linux so this drive is ready to use with it because it was not formatted to use with windows.. it has 1024mb of space saved for the swap, can i delete these 1024 mb (i prefer using the 17Gb for swap) and keep the rest of the data?remember, i need that data so, i need to be sure if i delete the swap, i will not delete all the data of that hard drive!

i really need a detailed description on how to do this, i already tried different ways to install it but, after selecting the partitions, it always says:"no root file system"

i need help on how to make the partitions and what options should i choose in each case.. hope someone can help me, i really want linux again.

---

### Post by arava on 2006-09-30
> **cmaranhao said:**
> 
i really need a detailed description on how to do this, i already tried different ways to install it but, after selecting the partitions, it always says:"no root file system"


I'm new to Linux, but have a possible solution as I've experienced the same issue.

While partitioning, look at the mount options. Change the partition you want Linux to be installed to "/" or root.
The partitioner seems to default to adding /media to existing partitions.

Hope this helps.

---

### Post by arava on 2006-09-30
> **cmaranhao said:**
> 
in the first partition, 12Gb will be enough, i want to instal linux.
in the second partition, 12Gb will be enough, i want to instal windows XP so that i can have dualboot (i need to work with a certain program that only runs in windows!)
in the third partition, i want to have it for saving files.


For you first question, I suggest you install Windows first. Windows (& MS) believes it is the only OS in the world. Through ignorance or arrogance it doesn't play well with pre-existing OSs. To start, it is best to let it believe it is the only OS on your computer. Then change things when it is not looking...

I'm not saying that you cannot do it your way, but it is easier (read, avoid other complications) to let Windows install first and then install any other OS.

---

### Post by cmaranhao on 2006-09-30
ok, but my main problem is how to setup the partitions on the linux instalation.. i just can't do it

i would be thankfull if someone helps me how to install linux the way i described (like, how should i set the partitions), if i have problems with windows later, i will do it all over again,(at least i practiced) with windows already installed.

---

### Post by cotcot on 2006-09-30
I recommend the Gparted LiveCD for partitioning.
Make a primary partition for XP (hda1).
Make a primary partition for Ubuntu (hda2)
Make an extended partition (hda3) for the rest of the disk.
Make a logical partition (hda5) for your shared files and a logical partition for swap.
Format hda2 and hda5 with ext3.
First install XP. XP installer will format the partition.
Install the ext2/3 driver in XP (see [www.driver-fs.org)](www.driver-fs.org)). It is simple to install.

---

