---
title: "Newbie"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by canada on 2005-05-16
Hello Everyone, i recently started to read about linux and the open source community and while i'm not a programmer i do enjoy the atomsphere of sharing and of no bounaries so to speak. I also have been using firefox for close to a year but it was only a few months ago i learn it was an open source technology. :) 

Well i have requested some free CD's from ubuntu or rather carniocal (spelling not sure) and while i wait for their delivery i want to get a good idea of how to install 2 OS's on my PC.

Any ideas where i should start i was looking for a sticky but there isn't one and the Doc's page on the main site isn't very user friendly.

Thanks in advance.

Newfie/Canadian :)

---

### Post by bored2k on 2005-05-16
There is no real "step" for this in Ubuntu. During the installation phase, you will be told "Found Windows XP OS, would you like to install a boot loader so this is possible?" You take the blue pill and you're set .

Screenshots on the scary -but easy- installer are here:
[http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1)

---

### Post by canada on 2005-05-16
So are you saying the installation disk will walk me through it or should i learn about paritions first because i like to kept my windows for now.

I've been using another distro (live CD) and reading the advantages of linux so i will be taking  the pill :grin:

---

### Post by Sam on 2005-05-16
Hello and welcome ! :wink:

For starting informations about your new Ubuntu, have a look here:
[list][*][Unofficial Ubuntu 5.04 Starter Guide](http://ubuntuguide.org/)
[*][Forum's index of HOWTOs](http://ubuntuforums.org/showthread.php?t=31094)
[*][Ubuntu Wiki](http://www.ubuntulinux.org/wiki/)[/list]

---

### Post by tread on 2005-05-16
You might want to read about resizing the windows XP partition (if your windows partition occupies the whole hard drive).
There are a couple of options there:
1. Buy and use something like Partition Magic
2. Boot from sysreccd or the Knoppic cd (both linux) and use qtparted (which has a partition magic type interface) to resize the partition.

I don't know if the ubuntu install/live cd contains parted ..

---

### Post by bored2k on 2005-05-16
[QUOTE=tread]You might want to read about resizing the windows XP partition (if your windows partition occupies the whole hard drive).
There are a couple of options there:
1. Buy and use something like Partition Magic
2. Boot from sysreccd or the Knoppic cd (both linux) and use qtparted (which has a partition magic type interface) to resize the partition.

I don't know if the ubuntu install/live cd contains parted ..[/QUOTE]
 Buy ? there are dozens of free or demo applications that do the same! Just get ultimatebootcd [google it] or a paragorn partition manager demo or somethiong.

---

### Post by bored2k on 2005-05-16
[QUOTE=canada]So are you saying the installation disk will walk me through it or should i learn about paritions first because i like to kept my windows for now.

I've been using another distro (live CD) and reading the advantages of linux so i will be taking  the pill :grin:[/QUOTE]
 Yes you need to have your partitions pre-configures before touching Ubuntu disc (unless Ubuntu takes over the whole drive). You might also think of the possibility of converting your NTFS partition to FAT32 (linux dislikes NTFS, has no write support for it..at least not that you will want to use).

---

### Post by jodef on 2005-05-16
[QUOTE=tread]You might want to read about resizing the windows XP partition (if your windows partition occupies the whole hard drive).
There are a couple of options there:
1. Buy and use something like Partition Magic
2. Boot from sysreccd or the Knoppic cd (both linux) and use qtparted (which has a partition magic type interface) to resize the partition.

I don't know if the ubuntu install/live cd contains parted ..[/QUOTE]I am always weary of suggesting Partition Magic as a partitioning tool on dual boot boxes, if you decide to use it just remember **never use partition magic on your linux partitions.** The Ubuntu installer will work fine for resizing as well. Regardless of what you use however always a good idea to back up your data first.

---

### Post by bored2k on 2005-05-16
[QUOTE=jodef]I am always weary of suggesting Partition Magic as a partitioning tool on dual boot boxes, if you decide to use it just remember **never use partition magic on your linux partitions.** The Ubuntu installer will work fine for resizing as well. Regardless of what you use however always a good idea to back up your data first.[/QUOTE]
 I second that opinion. Partition Magic doesn't even load my current HDD because of the (I presume) countless tweaking it has undergone. Most of the time I use paragorn on my Hiren's Boot disc v6. Works like a champ :D.

---

### Post by canada on 2005-05-16
Well guys thx for the help but of course i'm confused. I don't expect to be spoon feed or anything but i am very new to this. I believe i started to read about linux a week ago.

Are you suggesting that the ubuntu installer will do the job of keeping my XP system safe? 

I looked at the screen shots and said well that can't be too hard and then someone posted a guide which was a few 180's :) 

I'm thinking i will probably take it slow and play around with live CD's for a few years LOL

---

### Post by bored2k on 2005-05-16
[QUOTE=canada]Well guys thx for the help but of course i'm confused. I don't expect to be spoon feed or anything but i am very new to this. I believe i started to read about linux a week ago.

Are you suggesting that the ubuntu installer will do the job of keeping my XP system safe? 

I looked at the screen shots and said well that can't be too hard and then someone posted a guide which was a few 180's :) 

I'm thinking i will probably take it slow and play around with live CD's for a few years LOL[/QUOTE]
 Lol don't be afraid *spooky muziek plays*. Here's it goes:
Ubuntu installer will take care of dual booting, but before you load it up, you should already have your hard disk drive partitioned, so your Windows partition is safe. You need not to worry about the new partition type, because it will get changed by ubuntu. We'd be glad to help with any mo' questions ;).

---

### Post by canada on 2005-05-16
So what one do you recommend that works :)  You suggested one but agreed its not the best choice and i'm really don't want to buy one. Maybe i should get use to the system using the live CD and uninstall XP and have ubuntu by itself, who knows.

If i do get a demo i assume once my paritions are setup i have no use for the software for my purposes?

Thanks i really like this forum. Let's hope ubuntu gives gates something to think about :)

---

### Post by bored2k on 2005-05-16
[QUOTE=canada]So what one do you recommend that works :)  You suggested one but agreed its not the best choice and i'm really don't want to buy one. Maybe i should get use to the system using the live CD and uninstall XP and have ubuntu by itself, who knows.

If i do get a demo i assume once my paritions are setup i have no use for the software for my purposes?

Thanks i really like this forum. Let's hope ubuntu gives gates something to think about :)[/QUOTE]
 Forget about buying software. There are free demos of partitioning applications other than Partition Magic. I actually dislike Partition Magic. Once you get a hold of the demo and repartition your HDD, you can drop that software like a bad habbit !

I don't think removing Windows is going to work, specially by someone who has never used Ubuntu as his main system. You would start "how do I do this here, I can, wait aaaaahg!". It's a gradual process mate ;)

---

### Post by canada on 2005-05-16
Ok thanks i need to reparition the HDD. I will earch around for the software and use whatever one that suits my fancy.

BTW is that Creep's new album cover? Creep is an exceptional band.

---

### Post by bored2k on 2005-05-16
[QUOTE=canada]Ok thanks i need to reparition the HDD. I will earch around for the software and use whatever one that suits my fancy.

BTW is that Creep's new album cover? Creep is an exceptional band.[/QUOTE]
 No Lol. I don't even know who Creep is. What type of music is it ?
I just googled a creep image after listening to [Radiohead's creep](http://www.lyrics007.com/Radiohead%20Lyrics/Creep%20Lyrics.html) song :-P and GIMP'ed the ".creep" on the picture.

---

### Post by canada on 2005-05-16
LOL that's funny that's what i'm refering to Radiohead i use to play creep. **Radiohead** is an expectional band.

Time for bed i think. Thanks for the help i'm sure i'll be back :)

---

### Post by bored2k on 2005-05-16
[QUOTE=canada]LOL that's funny that's what i'm refering to Radiohead i use to play creep. **Radiohead** is an expectional band.

Time for bed i think. Thanks for the help i'm sure i'll be back :)[/QUOTE]
 *Thank you* for keeping me entertained :D.

---

