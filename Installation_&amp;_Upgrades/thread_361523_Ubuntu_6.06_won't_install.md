---
title: "Ubuntu 6.06 won't install"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by MarcusOConnor on 2007-02-14
first: i'm a total noob concerning linux, never worked with it before and I don't know anything about it, please be patient :grin:

I want to install Ubuntu to my extern 500Gb HD
my bios allows usb boot so i asume it is possible..

I partitioned it in the following sizes:
1)   -191,99 GB             FAT32            Primary partition (PP)
2)   -50,01 GB               FAT32            PP  (also marked (in vista)with 'active')
3)   -2,00 GB                Swap              PP
4)   -9,77 GB                FAT32             PP

(-212 GB                - - -               unallocated) 

The first two partitions were split out of one big 500 GB partition with Partition Magic 8, the other two I created out of the unallocated space using the Ubuntu Live-CD partitioning tool.

I want to keep the 1st partition for all my vista backups, the rest is available for linux
so during the setup, I marked the 2nd as root partition "/" , 3rd as Swap and 4th as /home
also selected all 3 partitions to be reformatted

when i start the installation, he starts running but after a few seconds he displays this error

[IMG]http://i12.tinypic.com/2gsr8ye.png[/IMG]
it's in dutch but the translation is: invalid filesystem for this <literally>attachmentpoint.</literally> 


Some useful info: 

-during partitioning 1 and 2 with PM8, i had a message telling me there were errors on a sector of my disk.
    exploring in windows could only show me the 191,99 GB of partition 1
opening the diskmanager i could see partition 1 (ok), 2 (no driveletter or filesystem shown) and the unallocated space (which was not intended)

starting it up again, PM8 showed a message reporting possible overlaying partitions and an option to fix it (I ignored it) 
partition 1 and 2 as 1 big partition (as if they were merged), marked only with 'Bad'
    Started PM8 again and clicked 'fix'. From then on, he showed (at last) the 1st (191) and 2nd (50 GB) partition.

afterwards, i realised that i ignored windows' warning that PM8 was possibly not compatible with vista :-\"

Do i need to reformat the partition in a different way?
Do i have to make new partitions?
Is the extern HD-boot thing actually possible,...

Any help would be MOST Welcome [-o<

thanks on advance,
Marcus

---

### Post by MarcusOConnor on 2007-02-14
Some new thoughts i had: 
- both partition 2 & 4 are displayed in the linux-partitionmaker as being 'locked' could that be a sign i set wrong options for the format?

- Partition 2 is marked as 'boot' or something...

---

### Post by housam on 2007-02-14
Ubuntu must be installed in a partition format ext3 for the root ( / ) and a swap format for the swap partition. So you need to create at least 2 partitions to install ubuntu. you can add another partition as /home for data/media storage ext3 format too. ubuntu partitions could be primary or logical , no problem about that.
Also use Gparted ( on the live CD )to partition your HDD , it is better in ext3 format.

---

### Post by MarcusOConnor on 2007-02-14
thx a lot, i'll try it right away

---

### Post by MarcusOConnor on 2007-02-15
Everything's running fine now, strange i didn't notice any other info on the necessary partition types.
anyway, ubuntu's install went just great from then on, only 6 min installtime =D>
The vista thing needed 25 times this long...    unlikely that it will be booted again soon ^^

thanks a lot

---

