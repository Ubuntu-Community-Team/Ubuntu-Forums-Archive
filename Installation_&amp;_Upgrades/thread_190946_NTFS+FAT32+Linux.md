---
title: "NTFS+FAT32+Linux?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by I3rianL on 2006-06-06
I'm completely new to Linux but I have been doing my research.  I think I read somewhere that you can have a FAT32 partition that can be accessed by both Windows and Linux on a dual boot computer.  Can someone confirm this?  Also if this is true, how do i go about installing my partitions?  I have a 80 GB drive and I want a 30 GB Windows partition, 20 GB shared, and 30 GB for Linux.  If I have a blank hard drive which OS should I install first?

Any help is greatly appreciated.

---

### Post by aysiu on 2006-06-06
Read these two links. You won't regret it.

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by rcarring on 2006-06-06
In answer to another question some one had, I suggested dividing the hard disk by percentage:

Hard Disk 80GB

40% Windows -- 32GB Primary NTFS

10% 'Shared' -- 8GB Primary Fat32

50% Linux including Swap. install into freespace.

Interesting article on Hard Disks here :

[http://www.ranish.com/part/primer.htm](http://www.ranish.com/part/primer.htm)

It does confirm that you cannot have more than 4 primary partitions on a hard disk.

---

### Post by LanDroid on 2006-06-06
I found this site quite helpful.  It's being reworked for Dapper.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This is probably the specific page you want:
> This install resizes the Windows NTFS partition to a smaller size to make room for the Linux partitions. Then it creates the Linux EXT3 operating system (root) partition (primary), and one FAT32 logical data partition. Finally, it makes the swap area (logical).

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)


---

### Post by rcarring on 2006-06-06
In case anyone wonders why my Fat32 shared partition is so small, here are the reasons:

a) Ever tried to back up an 80GB Fat32 shared drive easily? If we assume no DVD burner as an option, that is an awful lot of cds, and the only realistic option is a usb external hard disk that mirrors the fat32 partition.

b) If you are doing huge DVD movie edits using either XP or Linux then you need a very fast drive, maybe a scsi drive formatted either as NTFS or as EXT3.

c) The Linux swap is traditional stuffed at the end of the drive, this is okay if you have a fast hard drive (i.e. 7200 rpm minimum) but with slower drives you may want to put it in the middle of the hard disk.

d) If you have a 200GB hard disk don't go for huge partitions, they take ages to access, and dividing the drive up into smaller bites makes it faster as the heads dont have to scramble across the drive.

e) After a time every hard disk gets fragmented. Having a small Fat32 partition means you could if need be haul the data across to XP or indeed Linux and then reformat the drive, finally copying the data back.

f) Any XP system drive is going to have to be able to stand alone -- many programs install only to the system drive --- many use the tmp variable set to the users Documents & Settings folder.

g) Any hard drive can and will fail eventually. You could turn on your computer one morning and find your hard drive has died, and all those music downloads have disappeared for good. If you have a mirror of stuff you simply cant afford to find and download again, backed up you won't have to worry. 

8GB is a lot of data.

++

I have a 100GB external hard disk and no way to back it up, I use it as the backup to my laptop hard disk.

---

### Post by I3rianL on 2006-06-06
How big should the /home partition be compared to the Ubuntu partition?

---

### Post by rcarring on 2006-06-06
Taking my example above, and reckoning on a swap of 512mb...

Overall 40GB

Ubuntu System 10GB

Swap 0.5GB

Balance /Home

---

### Post by aysiu on 2006-06-06
[QUOTE=I3rianL]How big should the /home partition be compared to the Ubuntu partition?[/QUOTE] Read the first link I posted.

---

### Post by rcarring on 2006-06-07
With respect aysiu, you don't actually tell him how big to make his /home partition. I do.

One question, if I may? If the /home directory contains user data and user specific files, why would the /home partition be so gargantuan (if I understand your partition map correctly).

My rationale for the split of drive is based on my personal experience in how much room Ubuntu needs when installing packages. The swap is similarly defined (being 2 x ram).

I guess I could have said 29.5GB, but I assumed that he knew what I meant.

Thanks

---

### Post by aysiu on 2006-06-07
[QUOTE=rcarring]With respect aysiu, you don't actually tell him how big to make his /home partition. I do.[/quote] I understand that, but the whole point of that link is to explain the pros and cons of different approaches. A number is just a number. It's much better for someone to understand the rationale behind the partitioning schemes and then make up her own mind.

> 
One question, if I may? If the /home directory contains user data and user specific files, why would the /home partition be so gargantuan (if I understand your partition map correctly). The /home partition contains user data and user files--pictures, music, videos, documents, etc. Those take up a lot more space than just the programs and their libraries (which usually amount to no more than 4 GB). That's why I recommend it be so huge.

---

### Post by rcarring on 2006-06-07
Thanks for that. I have added some notes on a thread I think Herman has posted in, to allow him to debate my suggestions. These are of course all suggestions, some maybe made more emphatically than others.

I do think though that people seeking to do a more complex install, should use the alternate cd.

I also think that backing up one's data before resizing the drive is always a good idea, but may be inpractical due to a lack of an alternate storage source.

---

### Post by Herman on 2006-06-07
Hello, rcarring,
> I also think that backing up one's data before resizing the drive is always a good idea, but may be inpractical due to a lack of an alternate storage source. I agree 100% with that statement, I have only recently discovered how quick and easy it is to drag and drop files into a USB drive. I think USB storage drives are great, and now that hard drive prices are very affordable, I don't know why so many people still bother with CDs and even DVDs. USB storage drives are the way to go for sure!
> I understand that, but the whole point of that link is to explain the pros and cons of different approaches. A number is just a number. It's much better for someone to understand the rationale behind the partitioning schemes and then make up her own mind.The /home partition contains user data and user files--pictures, music, videos, documents, etc. Those take up a lot more space than just the programs and their libraries (which usually amount to no more than 4 GB). That's why I recommend it be so huge.I agree with Aysiu on this. I think a _P_ersonal _C_omputer is well named. One of the biggest reasons we like them so much is because they are so easily able to be customized to suit each of our own unique requirements. 
These individual wants and needs can vary so greatly between one person and another that I feel it is quite difficult to advise anyone on what sizes they should choose for disk partitions. Everyone has a different job or business, plus their own special interests and hobbies. I would need to know that person very well and sit down and talk it over with them for some time. I think Aysiu's approach is best, provide information that will help them think about it, and let each individual make up their own mind.
Well, :D back to my web-site editing, all the best, bye for now, regards. Herman

---

