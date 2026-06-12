---
title: "What to do to ensure that files can be shared between XP and Linux ?"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by noreaga on 2006-12-17
Hi everyone. So ive been reading a lot about Linux, and have decided to attempt creating a dual boot on my laptop with XP and Ubuntu.

Ive got a 100 gb HD, which is currently all used by WinXP. Im planning to do a 60gb (XP) / 20 gb (Linux) / 2 gb (swap) / 9 gb free space. For the partition, Im planning to use Partition Magic initially to resize the current XP size from 100gb to 60 gb. Ill then use the Ubuntu CD to boot from and install, and create the remaining partitions.

What Im interested in knowing is how to make sure that I can share files btwn the two OSes. Ive read a little on the fact that there might be some incompatability. Do I need to change the type (NTFS/FAT32) ? Do I need to edit a file after install ? 

Can I get some advice on what exactly needs to be done, and how, to ensure that files can be shared btwn the two OSes ? 

Also, if anyone wants to give any advice on the partition strategy, let me know :) 

Thanks all !

---

### Post by kpictjl on 2006-12-17
linux doesn't dig-on ntfs so as far as I know so use fat32 for the shared location.  Some distro's are playing with ntfs but we're not there yet.  The rub is that I can't figure out how to make xp format a partition as fat32....I don't even think that xp can run on anything but ntfs.

I'd go something like this...
20GB (XP) - ntfs, bootable
5 GB (Linux) - ext3, bootable
73 GB (shared) - fat32
2 GB (linux swap)

The linux.org has some guidance on this as well,
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

here's good how to list for setting up file sharing with window (eg. installing and configuring samba)
Edgy
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
Dapper
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by Wall86 on 2006-12-17
my windows xp pro, will format as fat32, and will even install in fat32(laptop came with xp installed on a fat32 file system), 

just use the disk management tool,

---

### Post by kpictjl on 2006-12-17
> **Wall86 said:**
> my windows xp pro, will format as fat32, and will even install in fat32(laptop came with xp installed on a fat32 file system), 
If that's the case then I'd make the xp partition fat32 as well...then you maximize sharing options.

---

### Post by dbw on 2006-12-17
Noreaga-
  I have seen many posts on these forums describing how to read ntfs partitions from Ubuntu, I don't know how effective they are, but you might try [this link]("http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support") on the Ubuntu document storage facility.  Note that the default partition type in Ubuntu is ext3, which I gaurantee Windows will not read.  I would recommend the following:

from 100gb:
Windows OS partition:   NTFS :       15 -20 gb
Ubuntu OS partition:     EXT3:         ~10 gb
Ubuntu swap:                           2x ram.
Data:                          FAT32:       ~60 gb
Free Space:                .........         ~10 gb

then put your "My Documents" folder in WXP on the data partition, and symbolic link it to your Ubuntu home directory.   This will allow you to access the same files from either windows or Ubuntu, but it will keep your configuration files for each safe from the other operating system.

symbolic link step in detail:

```
cd /data
sudo chown -R noreaga My\ Documents
cd /home/noreaga
ln -s /data/My\ Documents
```

Now, just be sure to save everything to My\ Documents!
(I have assumed that your account name is Noreaga)

---

### Post by noreaga on 2006-12-17
thanks for the replies everyone. i can change my current xp partition from ntsf to fat32 using partition magic. However, arent there major drawbacks to using FAT32 ? Or am I really misinformed :confused: 

Oh, and if the Linux installs as ext3, how do I go about changing it ? or, can i change the type before install ? If so, what should it be ?

I will follow the guides as posted, and see if I have any luck ;)

---

### Post by dbw on 2006-12-17
fat32 is in general worse in terms of stability and fragmentation.  If you don't have a problem w/ your current fat32 install, you could stay with it.  I would really recommend using ext3 for the Ubuntu system files, though.  Lemme know if my instructions didn't make sense - I can easily "enhance" them.

---

### Post by noreaga on 2006-12-17
^^ thanks, i will.

my current partition is NTSF though. So, are you suggesting to leave it the way it is , and stay away from FAT32 ?

Someone earlier posted a link that takes you to a guide which shows you how to make NTSF write capable in Linux, any comments on that ?

---

### Post by ricks1950 on 2006-12-17
You have 2 issues:

1.  Read NTFS files from Ubuntu 

2.  Read Ext3 files from XP

Writing to the foreign file system can be the third issue, but if you solve the first two, you are in business.

1.  Ubuntu will mount and read your NTFS files.  So if you are surfing in XP and find something you want for Ubuntu, you can go ahead and download it, and you can read it when you boot Ubuntu.

2.  Microsoft does not provide any drivers for foreign file systems, however, you can Google and find a couple of open source drivers for Ext2 and 3 that will allow you to at least read.  

I haven't dual booted for years, but when I did, that is what I used.  Once I could read Linux file systems from XP and NTFS from Linux, I had file portability.

FAT32 isn't worth the hassle, in my opinion.

---

### Post by dmartinsca on 2006-12-17
There is a driver available for Windows which allows you to read and write to ext2 or ext3 filesystems. You can find it at [http://fs-driver.org](http://fs-driver.org) . I use it on a regular basis and haven't had any problems.
Also, there is now a driver available for linux which allows read/write to ntfs partitions, it's called ntfs-3g and you can find it here: [http://www.ntfs-3g.org](http://www.ntfs-3g.org) and there is a good guide to get it working here: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by namaku.syntia on 2006-12-19
Hi,

I have identical problem. I'm dual booting. I use NTFS for XP and reiserfs for ubuntu. I have no problem reading NTFS from Ubuntu. But I can't read reiserfs from XP. Are there any drivers so I can read reiserfs from XP?

Thanks in advance..

regards,
Syntia Wijaya

---

