---
title: "Best filesystem for dual access?"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by Bagleemo on 2005-02-25
Greetings! 

I'm a fairly experienced ubuntu user trying to spread the word, and I need a little advice.  I've just built a computer for a photographer friend of mine - Athlon XP, gig of ram, Asus MB.  It has two drives - one for the Win2k and programs and another for photos and data.   After many proddings, my friend has agreed to let me put Ubuntu on it as well, so that when his 2k system gets nailed by malware he can still boot something.  Also he wants to try the gimp.  

I'd like to install ubuntu on the second disk to avoid a bad partitioning bug I encountered before.  It will have its own small partitions, but most of the disk will be then used for images.  What filesystem should I use on the image partition such that ubuntu and Win2k can both read it?  FAT32 would work but I've heard its not as reliable as NTFS - and the integrity of the images is of the greatest importance.  Can ubuntu read and write to an NTFS partition?  Is there another format that both can read?

Thanks !

---

### Post by anand on 2005-02-25
NTFS writing support in Linux is still pretty immature so I'd avoid NTFS if you can if you need write support under Linux.

FAT32 is the easiest choice since both XP and Linux support it and support in both OSes is very mature.

You can also try EXT2 and download an EXT2 driver for Windows such as this one:
[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

I've never used that though so you're own your own but it seems like it has full read/write support.

---

### Post by zcox on 2005-02-25
I'm not sure what the best filesystem is, but I do know ntfs is read-only from Linux.  See [this link](http://ubuntuguide.org/index.html#automountntfs) for info on mounting fat32 and ntfs partitions.

---

### Post by thestarman on 2005-02-25
I'd stick with FAT32 if you really must have **write** access from both OSs!  Either OS can be set up for reading from the other's NTFS or ext3 files systems, but writing has been either impossible or problematic for both from the competing OS. I've had a FAT32 partition for sharing files between Windows 98SE, Windows 2000 and Linux (various distros) for years without any problems.  Using FAT32 also means that just in case there are any problems with that partition, you have more choices for data recovery as well; though I do use NTFS for my Windows 2000 (OS) partitions.

---

### Post by tkiesel on 2005-02-26
FAT32 works like a dream for me.  I mounted it as /dual  

 :D

---

### Post by Bagleemo on 2005-02-26
Thanks everyone! Looks like there isn't a perfect solution. I'll have to format the image partition as ntfs and then make a little swap fat32 partition.

Instead of having all those partitions can I install ubuntu on a fat32 ? This would make the disc have the following:

swap partition for linux
fat32 (instead of ext3) w/ ubuntu on it 
ntfs partition for image data

Thanks

-A

---

### Post by njs12345 on 2005-02-26
[QUOTE=Bagleemo]Thanks everyone! Looks like there isn't a perfect solution. I'll have to format the image partition as ntfs and then make a little swap fat32 partition.

Instead of having all those partitions can I install ubuntu on a fat32 ? This would make the disc have the following:

swap partition for linux
fat32 (instead of ext3) w/ ubuntu on it 
ntfs partition for image data

Thanks

-A[/QUOTE]
 That's not a good idea, because FAT32 doesn't have permissions.. even if it did work (unlikely) then it wouldn't work very well at all ;)

---

### Post by Bagleemo on 2005-02-26
Ahh, thank you.  
So I'll make it:

swap
ext3/ w ubuntu
small fat32 partition for trading data between OSes
ntfs partition for images

Do I have to tell windows 2k to ignore the swap and ext3 partitions? Disable them or something? Or will it take care of itself?

Thanks!
-A

---

### Post by Jesus Franco on 2005-02-26
Windows wouldn't even recongise those partitions. So dont worry about it. Now I recomend you pick up Partition Magic because i can do exactly what you want perfectly. And that would avoid issues.  :D

---

