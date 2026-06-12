---
title: "Need help setting up partitions manually for new installation."
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by 666pluto2 on 2016-01-23
I'm currently running windows 10 64bit, installed on a Samsung EVO 240GB SSD, storing all the data on a 1TB HDD.
I would like to install Ubuntu 15 alongside it, but would like to place the main partition on the SSD and the rest on the HDD. maximum space i have on the SSD for Ubuntu partitions is 40GB, but would like to use less.
[Found this guide, which makes it pretty much clear]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"). but have a few questions just in case :-).


SWAP - will set it at 4GB since I have a 16GB physical memory, but Won't use Hibernate or memory intensive tasks. 

[LIST]
[*] can i place the swap on the HDD? that way i can set it to 20GB and use  Hibernate if needed. should it still be set as "Primary & begging of  this space"?
[/LIST]
 Root - what's a good balanced size for this partition, when I'm kind of limited on space on the SSD? 20-30GB will be enough without errors?? Will be mainly surfing the net and watching movies, but storage in the HDD. won't be gaming or using any intensive applications.
Home - will place it on the HDD, 100GB size. 
[LIST]
[*]is it possible to set this partitions as NTFS? so i can access it from windows 10 as well. or it has to be ext4?
[/LIST]
 
***should i set the SWAP Primary & begging of this space, while the rest set as Logical & begging of this space?


sounds right or I missed something?

[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]

[/URL]

---

### Post by howefield on 2016-01-23
I'd put swap on the HDD although wouldn't use anywhere near 20GB, with that much RAM you should hardly ever use it (but it is still useful to have).

You could consider putting everything on the SSD including /home but symlinking the users main home folders, eg, Documents, Downloads, Music, Pictures, Videos, ect to folders stored on the HDD. I do this also with browser and email profile folders plus a couple of other heavily accessed folders.

---

### Post by oldfred on 2016-01-23
I do the same as Howefield.
My SSD is 120GB and I use 25GB for / including /home. And about 12 or 13GB is actually used. My /home is 2GB of the  12 because of .wine and Picasa.

I do have a swap on every drive, but do not recommend hibernating especially with a SSD. 
Ubuntu does not need the Windows fixes of fast boot in UEFI and fast start or always on hibernation and boot just as fast as Windows.

Is system UEFI or BIOS? Just be sure to install Ubuntu in same boot mode UEFI or BIOS as Windows is installed.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by 666pluto2 on 2016-01-23
thank you for replaying.

the system is BIOS, doubled checked to be sure. when installing ubuntu, i never saw an options to choose between the two. it will be set to bios automatically or what?

doing what Howefield suggested seems simple enough. but just to be clear, when you say symlinking the main home folders, what does it actually mean? they will be linked to a chosen folders on the HDD, so all data downloaded to them will actually be stored on the HDD folders? if i understood it correctly, what's the easiest way to make this symlinking? I'm new to Ubuntu, hope its not to complicated.

oldfred, thanks for the links. i read most of them, but to be honest, i got lost along the way, seems to complex for me...

---

### Post by oldfred on 2016-01-23
It does require a few commands.
And I started simply with just a shared NTFS data partition back with XP.

You basically have to create a data partition, create mount point for data partition like /mnt/data, add entry to fstab, and add folders in data partition. Then you can link data partition's folders into /home.

I normally do the linking as soon as I install to be sure I still have no data in current folder like Music. Once you link to a folder in another partition old folder is gone. But it will not let you link to exactly same name, so you do have some protection.  So I make sure data is backed up or copied from folders in /home, delete folders like Music, Documents etc. And then link folders, Music, Documents, etc  from data partition.

---

### Post by howefield on 2016-01-25
> **666pluto2 said:**
> ... but just to be clear, when you say symlinking the main home folders, what does it actually mean? they will be linked to a chosen folders on the HDD, so all data downloaded to them will actually be stored on the HDD folders?

Yes, pretty much as oldfred, all I do is mount the Data partition (which already has the desired folders in it) in addition to the / partition when installing Ubuntu and then use the command..
 
```
rm -r Documents Downloads Music Pictures Videos && ln -s /Data/Documents/ /Data/Downloads/ /Data/Music/ /Data/Pictures/ /Data/Videos/ ~/
```

This removes the folders from /home and then links to the "replacement folders" on the Data partition. I symlink a few others as said somewhere above mainly for ease of sharing between different installs.

---

