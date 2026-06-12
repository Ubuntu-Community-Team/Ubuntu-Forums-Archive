---
title: "Help on setting up partitions (dual-boot)"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by not_cool on 2006-11-16
I just recently got a 160GB ATA hard drive and installed it as a slave to my 80GB Windows HD (I also have 200GB and 80GB external ones). I am going to install ubuntu on it but am not sure as to my partitioning layout. I will keep the 80GB drive as it is. On the 160GB disk I would like to have it setup like this (not sure about the order):

Location_____Type_____Size
/data_______FAT32____???
/home______ext3______???
/__________ext3______???
swap_______swap_____???

I have 1GB of RAM. I'm going to be using the alternate CD to install Edgy, and need to know a few things:

1. What order the partitions go in
2. What partitions should be primary, what ones should be logical
3. What size each partition should be, I have a lot of music and photos that I want to put on the FAT32 partition, including other things over time. The /home partition will be similar.
4. I assume that the / partition will be the bootable one?

This computer will have four users.

---

### Post by Herman on 2006-11-16
Location_____Type_____Size
/data_______FAT32____???
/home______ext3______???
/__________ext3______???
swap_______swap_____???

>  1. What order the partitions go inAny order you like, as far as disk order goes, it doesn't matter at all.
>  2. What partitions should be primary, what ones should be logical We can have up to a maximum of four Primary partitions, or three Primary partitions with one called 'Extended', because there are only four sixteen byte entries allowed in the DOS partition table. The 'Extended' partition can contian up to 63 'logical' partitions, as long as they are 'contiguous' (like a string of sausages). ie, we can have an area of free space between logical partitions, but if we create a primary partition in between the logical ones it will cause problems. 
With Partman in the 'Alternate' CD, the 'extended' partition will be automatically created as soon as you make a logical partition. You won't need to create one yourself. 
It doesn't matter if you make them all 'logical' or some Primary and some logical, any arrangement will work just the same.
>  3. What size each partition should be, I have a lot of music and photos that I want to put on the FAT32 partition, including other things over time. The /home partition will be similar. That depends on how many GB of music and photos you want to place in each partition. You can easily change your partition sizes later on at any time nowadays with [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"), so don't worry about it, just make them any size you like.
Your ' / '(root filesystem) partition should be around 5 GB or so, you could get away with as little as about 3.0, but you would want to allow room for installing more software. I'd suggest even up to 10 GB, since you have the luxury such a nice large disk.
>  4. I assume that the / partition will be the bootable one? That doesn't matter either. If you are using Grub, it moves the boot flag around wherever you need it automatically with it's 'makeactive' command. You only have to set the boot flag somewhere if you are going to use Lilo as a bootloader instead of Grub. Unless you have a special reason, it's best to use Grub.

>  This computer will have four users. You can create as many user accounts as you want.  Ubuntu and other Linuxes are ideal for  sharing between many users. You will find the flie permissions you can set are extremely flexible and adaptable to all your needs. 

In my first sig link (under this post) there is a home page and it has some illustrated examples of using the 'Alternate' CD for installing with. The first one is about 'Edgy', the second two are about 'Dapper'. You might like to look at there for an idea how the installer works if you have never used the 'Alternate' CD before.

Regards, Herman :D

---

### Post by PatrickV on 2006-11-18
Hi'm in ubuntu5.10's partition disks now.

Looking at IDE1 master (hda) - 20 GB Fujitsu MHT2020at, 
#1 primary 9.8 GB  ext3   /
   pri/log 9.8 GB    free space
#5 logical 378.3MB swap   swap

Anybody live to guide me for what? couple hours or less right now please?

---

### Post by PatrickV on 2006-11-18
Hi'm in ubuntu5.10's partition disks now.

Looking at IDE1 master (hda) - 20 GB Fujitsu MHT2020at, 
#1 primary 9.8 GB  ext3   /
   pri/log 9.8 GB    free space
#5 logical 378.3MB swap   swap

Anybody live to guide me for what? couple hours or less right now please?

Almost forgot: not dual-boot unless for another linux like dsl or slackware.

---

### Post by bulldog on 2006-11-18
> **PatrickV said:**
> Hi'm in ubuntu5.10's partition disks now.

Looking at IDE1 master (hda) - 20 GB Fujitsu MHT2020at, 
#1 primary 9.8 GB  ext3   /
   pri/log 9.8 GB    free space
#5 logical 378.3MB swap   swap

Anybody live to guide me for what? couple hours or less right now please?

Almost forgot: not dual-boot unless for another linux like dsl or slackware.

Well what is your problem?
I presume you want to use the 9.8Gb of free space?
Download the gparted live cd and boot from it.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Now you may decide what you want to do with it,make a separate home,or a data partition,it's all up to you.
Just take your time to think things over.

---

