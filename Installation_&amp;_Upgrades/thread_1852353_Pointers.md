---
title: "Pointers?"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by Baalzebub on 2011-09-30
Hello all!

Id like to say first that I'm slightly new to Linux in general. I like to consider my self a geek but I've always kept my knowledge to windows OS's. Well due to a nasty virus i received on my computer a few days ago i decided to take a head dive into Ubuntu 11.04 x64. I have watched a lot of videos and read quite a large amount of information considering I only installed this a few days ago. I do have some experience with Red Hat 5.5 my job had me go to a 2 week course where the gear we worked on used Red Hat on its admin laptops. Also, my english and spelling are horible, i will use auto-correct as much as possible and attempt to make this legible. 

OK, now for my actual question/problem. 

So, when I built the computer that I am currently running I was planning on running windows 7 (which I understood was 27GB) and SSD's were semi-new. So in my mind I found it ingenious to buy a 30GB SSD and install windows on it, and put all of my data on to a seperate D drive that is 1TB. I quickly relearned that this wont work, if you sit down for 5 minutes you'll see why it wont but I wasn't thinking too well that day i guess. So i have a 30GB Solid State, a 1TB internal, and an external 3TB.

As i did some research into Ubuntu i found out it is a very small OS so i installed it on top of my infected C drive. This worked great for about 2 days but im already down to ~340MB of free space. So i was sitting here thinking of 2 different things, I have never attempted either. 

1) Can I download some form of RAID software and turn my 30GB SSD and my 1TB (internal) into a single logical drive?

2) Can i turn my SSD into a pointer device and have it point at the 1TB HDD for everything it needs except for swap, /, and maybe home?

I would prefer to go with the 2nd option, have it point at my 2nd hard drive to save everything onto and point at the 2nd hard drive for all data it needs to call on. I say i would prefer this because if i could (in theory from what i understand) boot into Ubuntu on the SSD (speed) and save its life a good bit by not making nearly as many read/writes to it. 

My other option would to be to install Ubuntu onto the D drive and just boot into it every time i boot my computer. 


I have my Ubuntu 666.10 (11.04 Satanic Edition [i love the theme!]) Live CD and i can easily put my GParted onto a CD. I run in classic mode not in normal because i instantly hated Unity. 

Help me out here guys-n-gals!

---

### Post by bhaverkamp on 2011-09-30
Ubuntu would fit nicely on a 30 GB drive. The pointers to which you refer are called soft links in Linux (and most UNIX like OSs). So yes you can keep the root on the SSD and link various subdirectories to directories on the spinning disk.

---

### Post by Baalzebub on 2011-09-30
Ok, so i did some real fast research on "Soft Links". 

How would i actually implement this?

open terminal and create a soft link to a make believe dir on the D drive and it will populate there? 
or copy the files over to the D drive, then make soft links to those files in terminal and delete the originals?

---

### Post by Baalzebub on 2011-09-30
Ok, the more i read the more confused i get by this...

[LEFT]  ln /original/file /new/link [FONT=Verdana,Arial,Tahoma]

[/FONT]THIS creates a Symbolic Link which from what ive read from a few sources basically is nothing but a exact replica of the original with a different name. if you edit 1 the other changes as well. 
[/LEFT]
  
 ln -s /original/file /new/link
[LEFT]This is a Soft Link which points a blank file at the original (equivalent to a shortcut in windows?)


So shouldn't i be able to us a ln -s /original/file /new/link and put the original file inside of my D drive and the link on the SSD this way when it goes looking for say the /var/log it will see the soft link and go to the ACTUAL file on the "spinning disk" 

PLEASE CORRECT ME IF IM WRONG I DON'T WANT TO MESS THIS UP. 
[/LEFT]

---

### Post by pjd99 on 2011-09-30
Answers to your questions:

1) No. It may be possible techncally, but you'd lose all the benefits of the SSD and might-as-well just remove it.

2) Pointers/simlinks is the wrong approach here, you're better off setting up the partitions correctly.

I'd put / and swap on the SSD, and keep /home on the 1TB. You don't need pointers/symlinks to do this, as the system doesn't care about the physical device as much as the partition make-up. Multiple partitions and multiple drives are indistinguishable from a "directory tree" POV, in the sense that any directory (except for the specials like /proc) could be a different partition or physical drive.

---

### Post by Baalzebub on 2011-09-30
> **pjd99 said:**
> 
I'd put / and swap on the SSD, and keep /home on the 1TB. You don't need pointers/symlinks to do this, as the system doesn't care about the physical device as much as the partition make-up. Multiple partitions and multiple drives are indistinguishable from a "directory tree" POV.

Ok, so keep my / and swap on the ssd and MOVE everything else over to the other drive? its already formated to ext4...

---

### Post by pjd99 on 2011-09-30
> **Baalzebub said:**
> Ok, the more i read the more confused i get by this...

[LEFT]  ln /original/file /new/link [FONT=Verdana,Arial,Tahoma]

[/FONT]THIS creates a Symbolic Link which from what ive read from a few sources basically is nothing but a exact replica of the original with a different name. if you edit 1 the other changes as well. 
[/LEFT]
  
No. cp will create a replica. ln creates a "Hard link". A hard link is pointing to the same data bits (i.e. the same inodes). IIRC, if you delete the original, you haven't really deleted it, because the linked file IS the original file. All you do there is remove one of the links to the data bits.
 > **Baalzebub said:**
> Ok, the more i read the more confused i get by this...
[LEFT]So shouldn't i be able to us a ln -s /original/file /new/link and put  the original file inside of my D drive and the link on the SSD this way  when it goes looking for say the /var/log it will see the soft link and  go to the ACTUAL file on the "spinning disk" 
[/LEFT]

ln -s creates a symbolilc link (i.e. essentially a shortcut, but more transparent than the .pif's in Windows). Instead of pointing to the original file's data, it just contains the location of the original file.

You need to have the directory structure set up before creating the symlink. If you move the original after creating the link it will no longer work (orphaned). They can't dynamically update themselves.

---

### Post by pjd99 on 2011-09-30
> **Baalzebub said:**
> Ok, so keep my / and swap on the ssd and MOVE everything else over to the other drive? its already formated to ext4...
That will probably cause a whole lot of mess. To do it properly, you might have to reinstall and manually edit partitions.

e.g.
SSD:
allocate 1x-2x your amount of RAM for swap.
(optionally allocate a few hundred MiB for /boot)
allocate the rest for /

Internal 1TB
allocate ~100-300GiB for /home
allocate the rest for storage /anameofyourchoosing

You might want separate /usr and /var mount points, as some of this data changes often, and I don't know if you'd want it on the SSD.


Moving the data will be very tricky, and best done using another system i.e. plug the drives into another computer so you can manipulate the data without worrying if it is being accessed at the time. Once it's moved, the directories that were moved will need a link created on the SSD (/) in the appropriate place. e.g if you move /home to /storage/home, you'll need a link place on /.
```

ln -s /storage/home /home

```I don't even know if the system would be usable after this, as I don't know how symbolic links are handled by programs if used in this way.

---

### Post by Baalzebub on 2011-10-02
Ok, so i did a fresh install instead (origionally planned on just saying screw the SSD and use the D drive) 
but as i was setting up my new install i knotised i could choose my mounting points and where to put them. in the GUI. 

so this is what i did: 

[B][FONT=Arial][SIZE=2] /dev/sda (SSD 30GB)
 /dev/sda1  /            2998MB
 /dev/sda6 /boot      1499MB
 /dev/sda7 /var        9513MB
 /dev/sda5 SWAP    16000MB      (2xRAM)
 /dev/sdb (100GB Partition of the 1TB HDD)
  /dev/sdb2 ext4 /home 21606MB 
  /dev/sdb5 ext4 /tmp 4998MB 
  /dev/sdb6 /usr        78252[/SIZE][/FONT][/B]

this works very well so far :D i ran into a few small problems but it was an easy work around.

---

