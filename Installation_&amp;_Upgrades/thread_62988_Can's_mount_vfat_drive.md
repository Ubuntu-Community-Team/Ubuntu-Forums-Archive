---
title: "Can's mount vfat drive"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by n!x on 2005-09-06
I have a problem mounting my other partitions on my harddisk. I have the biggest partition as vfat.

This is my fdisk -l:

```
Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot         Start         End      Blocks    Id  System
/dev/hda1             574       14596   112639747+   5  Extended
/dev/hda2   *           1         573     4602591   83  Linux
/dev/hda5             604       14596   112398772+   b  W95 FAT32
/dev/hda6             574         602      232879+  82  Linux swap / Solaris
```

when I try to mount my /dev/hda5 i type:

```
sudo mount /dev/hda5 /media/data -t vfat -o umask=0222
```

I get this error message:

```
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

When I try: ```
dmesg | tail
``` 

I get:

```
FAT: bogus number of FAT structure
VFS: Can't find a valid FAT filesystem on dev hda5.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hdb5.
FAT: bogus number of FAT structure
VFS: Can't find a valid FAT filesystem on dev hda5.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hda1.
FAT: bogus number of FAT structure
VFS: Can't find a valid FAT filesystem on dev hda5.
```

I have also tried to edit my /etc/fstab so the partition should mount at startup - but won't.

I have tried to search the Ubuntu forums but without any luck, it seems to me that many of you guys have had the same problem, but there's never an answer to it ??

So please help me - I'm ready to try to format my drive again, but I only have a headless Ubuntu-box. I'm not really used to fdisk  so if I have to format again it coukd be nice if anyone could guide me....

Thanks in advance!

/n!x

---

### Post by Jujimufu on 2005-09-06
[QUOTE=n!x]
when I try to mount my /dev/hda5 i type:

```
sudo mount /dev/hda5 /media/data -t vfat -o umask=0222
```
[/quote]

Try just typing:** sudo mount /dev/hda5 /media/data**

Also, don't feel stupid if you forgot to make a directory called */media/data*

**sudo mkdir /media/data**

Your fstab should have an entry looking like this:

/dev/hda5    __________       /media/data    ____________          vfat    ______________           defaults,users,auto,**rw** __________  0 __________    0

(Replace ________ with white space)

--------------------
Anyway, sorry if this doesn't help.  I'm not by any means good at this stuff, but I have mounted a serial ATA drive twice in the past week (twice because I fucked up something and had to reformat).

---

### Post by n!x on 2005-09-07
Thanks for the answer, but I tried all of what you said - but nothing helped. And yes I'm sure that I have a folder called /media/data.

Anyone else?

---

### Post by lol on 2005-09-07
[QUOTE=][/QUOTE]
 are you sure that the partition is ok? I mean, is it a working Windows partition for example? Or is it a partition that you created in Linux and never used before? Because if that's the case, you should probably try to reformat it again, something seems to be wrong with it.

So if you don't have any data on this partition, I would suggest:
mkfs.vfat -c /dev/hda5

oh! I just realized! Your partition is more than 32Gb right? That is probably the problem... you should try to find how to create a FAT32 partition of more than 32Gb on Google (it's possible, I did it, but honestly I don't remember how :( You may have to use some advanced tool like partition magic or partition expert...)

---

### Post by n!x on 2005-09-07
Thanks everybody for the suggestions - I gave it up and formatted the disk and installed Ubuntu on 1 partition. So now I have one big disk....

---

### Post by Steve1961 on 2005-09-07
Are you sure you can only create 32gb fat32 partitions?  I've got an 80gb fat32 partition that mounts with no problem whatsoever.  Perhaps you just need to enable large disc support in the bios - I think the option's LBA.

---

### Post by lol on 2005-09-08
Well, my mistake, I wasn't clear enough. The thing is: Windows (2K or XP) does not allow the creation of FAT32 partition > 32Gb (but can use bigger ones), and scandisk does not support partition bigger than 128Mb or something like that.

Now, when I first created my 60Gb partition, I did it under Linux, and formatted it (successfully) with mkfs, but I couldn't mount it or use it, whereas I never had this problem before with smaller partitions. I am also quite sure that it has nothing to do with the bios. It's really a pity that I don't remember how I finally solved this...

---

