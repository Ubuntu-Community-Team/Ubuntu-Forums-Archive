---
title: "A few unanswered questions:"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by solaceinsilence9 on 2008-03-25
First and foremost, Im new to Ubuntu. So this is a somewhat alien experience seeing how I had almost no Linux experience prior to a friend recommending a Ubuntu install on my 1501. I am computer inclined, so I do have an idea about this. Most of my questions are from lack of experience. So let me start with my situation. I installed Ubuntu 7.10 on my 1501 yesterday and I love it! I decided to make the move from Vista to Ubuntu so I did a SMALL 10gb partition of Ubuntu to get used to the new OS.

First question. Ubuntu requires two partitions. One the main and the other the swap. Am I correct to assume that main is the system partition for the actual OS and swap is for user stored files?

I am in the process of configuring Ubuntu for my 1501. That means setting up the resolution and the wireless, etc. That I can do myself and I want to make sure I can do all of that before I do a full wipe of my harddrive and reinstall Ubuntu with larger disk space. Im new the the whole partitioning thing. I can see how it benefits having more than one partition to protect your data.

Second question. When I reinstall Ubuntu whether it be 7.10 or the newer version that is in beta testing, how would you recommend me setting up the partitions? When all is said and done, I want to be able to dual boot Vista and Ubuntu. I know what you are thinking, why Vista? Well simply it came with my laptop and I need it for some of my college classes anyway. But I do want a SMALL partition of Vista but, Ubuntu will be the primary OS used on the laptop.

Third question. I also want to set up separate partitions for my documents that I can access on both OS's. How do I do this? I noticed that even though Ubuntu can see the partition Vista is using it cannot access the files. Is this because they use a different file system? 

Anyway, thanks in advance for the help. Ubuntu is my new fav OS and I want to be able to take full advantage of it and eventually contribute in some manner.
:guitar::lolflag:

---

### Post by scragar on 2008-03-25
swap is like extra ram to be used if you run out, it's possible to do away with it completely, however I don't think there is anyone who would recomend it(although having said that youtube did well with that very idea).

I have 2 HDs, and my partitions are set up as:
```
hda1 = windows XP = never used :P
hda2 = ubuntu 7.10 = main system, yeah!
hda5 = swap

hdb1 = /home/**username** in ubuntu, just seen as a second HD in XP - can't remember format, but proberly fat since windows can access it as well
```

---

### Post by phidia on 2008-03-25
Just to add a little more /home is the area your install uses for user files ( /homeyourusername ).
You can get linux to read ntfs go [here]("http://www.ntfs-3g.org/")and windows can also fairly easily [read and write]("http://howtoforge.com/forums/showthread.php?t=1097") to ext3.

---

### Post by scragar on 2008-03-25
ooh, definatly teach windows to read the etx formats, the permitions and lack of need to defragment makes them far superior to fat or ntfs.

---

### Post by solaceinsilence9 on 2008-03-25
Well thanks for the speedy replies! So the main partition is where the the OS is stored as well as your personal data. So if I decided to partition another section of my drive for say music, and I used the ext3 format Ubuntu wouldn't have a problem reading that partition? I would then have to use that article to get Windows to read ext3 so that I could use those mp3 or ogg files in Vista also. Ok, I think im getting it now. Another thing to note, if I have a gig of RAM and I partition the swap to also have a gig will Ubuntu have a total of 2 gigs of RAM to use? 

I think I might lay out my hard drive like this:

XP or Vista 10gb partition (NTFS)
Ubuntu main partition 45gb (ext3)
Swap partition 1gb (ext3)
Music and other data partition 20gb (ext3)

For a total of 76gb on my 80gig hard drive.

The other four gigs I left because I was told that even though harddrive are marketed at 80 or 120 etc you arent actually getting a full 80gig harddrive. Does that look good or am I still missing something with the partitions?

---

### Post by phidia on 2008-03-25
> **solaceinsilence9 said:**
> Well thanks for the speedy replies! So the main partition is where the the OS is stored as well as your personal data. So if I decided to partition another section of my drive for say music, and I used the ext3 format Ubuntu wouldn't have a problem reading that partition? I would then have to use that article to get Windows to read ext3 so that I could use those mp3 or ogg files in Vista also. Ok, I think im getting it now. Another thing to note, if I have a gig of RAM and I partition the swap to also have a gig will Ubuntu have a total of 2 gigs of RAM to use? 


swap is obviously memory on your hard drive you only want to use that when you run out of ram because it will be slow-really slow. So you can say you'll have 2 Gb but really ram is ram using hard dirve space for ram is slow.

> **solaceinsilence9 said:**
> 
I think I might lay out my hard drive like this:

XP or Vista 10gb partition (NTFS)
Ubuntu main partition 45gb (ext3)
Swap partition 1gb (ext3)    
                    

swap is it's own format not ext3 the installer takes care of that though so not to worry

> **solaceinsilence9 said:**
> 
Music and other data partition 20gb (ext3)

For a total of 76gb on my 80gig hard drive.

The other four gigs I left because I was told that even though harddrive are marketed at 80 or 120 etc you arent actually getting a full 80gig harddrive. Does that look good or am I still missing something with the partitions?

Seems ok take a look at notes i entered above-good luck.

---

### Post by scragar on 2008-03-25
to be honest I have a gig of ram, and never need swap(which is why my swap is set to 256MB), so unless you do a lot of ram heavy activities I wouldn't worry about having such a large swap(you can tell when your using swap, things start running slow because it's moving things to and from the hd instead of the very fast ram).

other thing I would love to point out is that you don't need 45Gb for ubuntu, my whoe install is a little over 5GB(including ton's of applications, several games, a full apache install etc), so I can't image you needing anything more than 10 or 15GB for your ubuntu install, esspecialy if you mount your music-etc partiton as your home folder.

---

### Post by solaceinsilence9 on 2008-03-25
Ok. The only reason I allocated so much space for the main partition for Ubuntu is because it is simpler for me to give that much for the partition to get rid of the extra hard drive space. And I see what you mean when you talk about the 1gig of swap memory. I just used that much because I am still use to Vista using nearly 85% of my RAM for simple tasks. Which is completely bogus in my opinion. Just after boot without anything running except for the few task manager programs it says around 50%. I was actually considering upgrading to 2 gigs before i found ubuntu. But that is beside the point. Anyway though, thanks again for the help, I really do appreciate the extra information.

---

### Post by zvacet on 2008-03-25
You don´t need 45GB for root partition.Let say that 10Gb should be good choice(depends what are you planing to install and run) but if you gat to hte situation that you need more space on root you can easy resize it.I will do thatt this way 

1. root = 10GB                                        mountpoint /
2. swap = 1GB
3. home = rest o free space                   mountpoint /home


Optionaly you can make another one just for music or something else you are interested in and call that partition let say storage.This is optional because you can save all your files at home partition.You can read more about partitioning [here.](http://www.psychocats.net/ubuntu/installing)

---

### Post by solaceinsilence9 on 2008-03-25
Ok thanks ill check out that article. Im still not sure how linux works in general, I am assuming that the installation files for various programs stay in the main partition. But what you are saying makes sense.

---

### Post by zvacet on 2008-03-26
>  I am assuming that the installation files for various programs stay in the main partition.

Yes,that is the case.But settings and your private data are on home partition,and that is why is good to keep it separate.In case of reinstall or something else you will not touch your home partition and that way you will save settings and files.

---

