---
title: "PartitionMagic Users SG"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by stewjack on 2006-11-28
**This thread is for people who have had experience using PartitionMagic, and want to compare experiences.  Everyone seems to know that something is wrong with PartitionMagic, - but no one knows what!** -](*,)   

My Experience :???: 
I have used PartitionMagic regularly with Windows for over four years. When I decided to seriously check out Linux I upgraded to PM8 specifically because it claimed to handle ext2, ext3, and Linux Swap partitions.

No luck!  Apparently gParted recognizes PM's partitions, but PM doesn't recognize gParted's partitions. At least not those formatted and made bootable by QParted.  At least that was my experience when running WIN98SE.  

I also lost Grub,but not until I ran my original PM7.  It automatically "fixed" my Linux partitions because it didn't recognize them.  Somehow that broke Grub, and required a [fdisk /MBR].  Not that my Linux would have booted after having it's partition "fixed."  That is why I got the wonderful PM8.

Anyone else with experience of PartitionMagic out there.

Jack

---

### Post by jazzgossen on 2006-11-28
With Ubuntu, there is no need to use PM. Use gparted (included on the live CD and in the repositories) instead.

---

### Post by RJARRRPCGP on 2006-11-28
> **stewjack said:**
> **This thread is for people who have had experience using PartitionMagic, and want to compare experiences.  Everyone seems to know that something is wrong with PartitionMagic, - but no one knows what!** -](*,)   

My Experience :???: 
I have used PartitionMagic regularly with Windows for over four years. When I decided to seriously check out Linux I upgraded to PM8 specifically because it claimed to handle ext2, ext3, and Linux Swap partitions.

No luck!  Apparently QParted recognizes PM's partitions, but PM doesn't recognize QParted's partitions. At least not those formatted and made bootable by QParted.  At least that was my experience when running WIN98SE.  

Your experience seems quite different.  I also lost Grub,but not until ran my original PM7.  It automatically "fixed" my Linux partitions because it didn't recognize them.  Somehow that broke Grub, and required a [fdisk /MBR].  Not that my Linux would have booted after having it's partition "fixed."  That is why I got the wonderful PM8.

Anyone else with experience of PartitionMagic out there.

Jack

--

---

### Post by RJARRRPCGP on 2006-11-28
> **stewjack said:**
> [B]
No luck!  Apparently QParted recognizes PM's partitions, but PM doesn't recognize QParted's partitions. At least not those formatted and made bootable by QParted.  At least that was my experience when running WIN98SE.  


Partition Magic is picky!! 

It may display fictuous partitions for no apparent reason.

Partition Magic sometimes don't like it when I don't wipe the HDD with zeroes. 
It may have a hissy fit by giving the dreaded "Error Sector not found" pop-up or it displays a bogus partition.

---

### Post by bulldog on 2006-11-28
I have used PM8 in windows XP many times,and even made some partitions with it,to install Fedora.
Never had big problems with it though.
Did what I expected it should do so no complains about it.

Now I use the Gparted live cd and it does the job as well.
And it's free to download so the choice shouldn't be difficult.

---

### Post by stewjack on 2006-11-28
> **bulldog said:**
> I have used PM8 in windows XP many times,and even made some partitions with it,to install Fedora.
Never had big problems with it though.
Did what I expected it should do so no complains about it.

How did you manage to escape using the formatter that came with the Linux distribution? I am not familiar with Fedora.  However, I have never been able to do a HD  install of  Linux in the partitions created with PM.  At the very least the installer always formats the the boot partition. It's after the Linux program creates a partition or just formats a partition that PM gives me problems.

> **bulldog said:**
> 
Now I use the Gparted live cd and it does the job as well.
And it's free to download so the choice shouldn't be difficult.

I have the gParted live cd, and no it doesn't do the job (maintaining my many XP partitions) as well as PM.  The whole point of this thread is to discover how both programs can live together! ](*,) 

I am glad that your experience indicates that they can do so.

---

### Post by akshaysrinivasan on 2006-11-29
Why would anyone bother buying Partition Magic ,when gparted ca do it for free??

---

### Post by bulldog on 2006-11-29
You can't skip the format option,but in my first Linux experience I wanted to make my partitions inside windows,to be sure it was the way I wanted them.
So I used PM8 to do so.:D 

Now I have learned how things go in Linux,I feel comfortable with gparted live cd,so I never use PM8 again.

I have a 30GB windows XP,which I only use to play a game once in a while,but I use Ubuntu for anything else.
I have a Dapper install for safety,and a 30GB Edgy running quite well so I don't need to use PM8 anymore.

---

### Post by stewjack on 2006-11-29
> **bulldog said:**
> You can't skip the format option,but in my first Linux experience I wanted to make my partitions inside windows,to be sure it was the way I wanted them.
So I used PM8 to do so.:D 

Now I have learned how things go in Linux,I feel comfortable with gparted live cd,so I never use PM8 again.


If that is true then I guess that it is still possible that if you did start up PM8 it would read your gParted formatted partitions as corrupted - if not the entire disk. Your experience neither contradicts nor confirms my understanding of the nature of the software conflict.

While trying to work around this problem, I am running a distribution called Puppy in persistent LiveCD mode.  It stores my personal settings in a large 3FS ?? file that is stored in a FAT partition. Dapper Drake also has a persistent option and maybe something similar can be accomplished. But all that's for later. I think that I will have to understand the differences between creating a partition, formatting a partition, and creating a file system. What's the difference between formating a ext3 partition, and  mkfs ext3, or something like that?

Jack

---

### Post by bulldog on 2006-11-30
Well it's possible PM8 would see my partitions created with gparted as corrupted,I don't really know.

I haven't PM8 installed so I can't take a fast look at it.
The difference between formatting a partition as ext3 or use mkfs,I can't tell you either.

I use the Gparted live cd to partition my drives and format them again when I install a distro.

If I remember correctly,I stopped using PM8 because it couldn't resize ext3 partitions or having trouble with the swap or something like that.
There was something I couldn't do without errors so I didn't use it anymore.

---

### Post by timcredible on 2006-11-30
i've used pm in the past, but why use it now?  gparted and qtparted are great, and as far as i can tell, it's better than pm.

---

### Post by bulldog on 2006-11-30
> **timcredible said:**
> i've used pm in the past, but why use it now?  gparted and qtparted are great, and as far as i can tell, it's better than pm.

Yes,go on,**why is it better as Partition Magic and what's wrong with PM?**that's what OP like to know.

---

### Post by Herman on 2006-11-30
GParted and QTParted and Partman, (the disk partitioner in the Ubuntu 'Alternate' CDs), are all good open source disk partitioning applications which are based on [GNU libparted]("http://www.gnu.org/software/parted/"), 
Because they are all 'Parted based , they are all fully compatible with Grub and other open source software. They were made with that specific objective as a priority, and most Gnu/Linux distros and software is designed to be compatible with [GNU libparted]("http://www.gnu.org/software/parted/"). 
To demonstrate what I mean, try ```
sudo parted
``` Does something happen? Yes, you have a 'Parted shell, you can type 'help' for a list of commands you can use. \\:D/

Now try, ```
sudo partition magic
``` Does it work ? No? :-({|= Partition Magic is not recognised by Gnu/Linux distributions, and is a foreign or alien utility.

Partition Magic is primarily designed for use by Windows users and for Windows based computers.  Probably it would be very good for that, I would not know, I have never used Partition Magic, unless it's in that Windows XP 'Disks Management' utility, I tried that out once or twice quite a while ago. 
Here is a link I rather like on this subject, [Partitioning Tools ( And which ones not to use )]("http://www.brunolinux.com/04-The_File_System/Partitioning_Tools.html")
I would suspect that it would be the similar to many other commercial Windows utilities, and be designed to take your money as another of its prioritities too, and it would be quite good at that as well. That is why they don't have their own web forum open to the public view. No-one can see the number of problems, errors and and bugs they have, it's all kept secret, 'behind closed doors'.  Can you give me a link to the Partition Magic Web Forums? 

Here is a link to GParted LiveCD's web forum, where you can get free help if you need it, [http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/)
The real reason why I like GParted, is the because of the great people behind it. A long time ago I when I was using the 'Alpha 3 0.0.9-' GParted LiveCD, I found it didn't work on my old test computer's video card, so I made a bug report to let the developers know. I received a freindly personal email response from the GParted developers and the next version of GParted worked properly in my old computer. I don't imagine I would have been given the same personal attention if I had been using a commercial disk partitioning software. The GParted developers are also member of Ubuntu Web Forums and occasionally answer posts here too, not so often now that they have their own forum to keep them busy though. 

These are some of the reasons why I feel GParted is the best.

My 2 cents worth,
Regards, Herman :-D

---

### Post by stewjack on 2006-12-01
> **bulldog said:**
> Yes,go on,**why is it better as Partition Magic and what's wrong with PM?**that's what OP like to know.

I have six Windows partitions to maintain.  I dont want to get out of windows to boot up the gParted LiveCD.  Computers are used by diferent people in different ways. 

Plus - SUSE version 9 had a bug in its partitioner that changed the geometry of all partitions on the disk.  It destroyed most Windows setups, but PM7 was able patch things together for me.   

Many of my experiences with PM8 were on that patched and unstable disk, so I am uncertain if all the problems I have experienced with PM8 are real.

This thread was for people who would like to discover the specific problems PM8 has.  It was not for people who didn't care if PM8 had problems.  This thread is for people who are interested in, or have have had experience with, - PartitionMagic!

The Title of the thread was supposed to be **PartitionMagic Users SIG** (**S**pecial **I**nterest **G**roup)

---

### Post by Joedude on 2006-12-02
I used to use PM8. I quit with the CD version because I always got strange errors...like above. I then had it make the 2 disk boot floppies. It ran great, except, it loved to be picky. If I didn't wipe the MBR on a dual boot or a system I was setting up for dual boot, or a system which was all ready dual boot, it always gave me corrupt boot sector warnings. 108 I think.

The only major problem I had was PM8 could never do a swap partition properly. Whatever distro I put on there it was fine with the ext2 or ext3 formats, but always hated the swap. So, for reasons I don't even understand. I would partition and format everything the way I wanted it, load up the install cd for whatever linux I was using, then allow the install cd to repart and format it again. 

Obvious problem is why? Whay do it twice? Well, sometimes it just didn't work properly unless I pre partitioned the hdd first. I no longer use any version of PM. So I think that's about all I can contribute.

---

### Post by Herman on 2006-12-02
> **This thread is for people who have had experience using PartitionMagic, and want to compare experiences. Everyone seems to know that something is wrong with PartitionMagic, - but no one knows what!** -](*,)   

My Experience :???: 
I have used PartitionMagic regularly with Windows for over four years. When I decided to seriously check out Linux I upgraded to PM8 specifically because it claimed to handle ext2, ext3, and Linux Swap partitions.

No luck! Apparently gParted recognizes PM's partitions, but PM doesn't recognize gParted's partitions. At least not those formatted and made bootable by QParted. At least that was my experience when running WIN98SE. 

I also lost Grub,but not until I ran my original PM7. It automatically "fixed" my Linux partitions because it didn't recognize them. Somehow that broke Grub, and required a [fdisk /MBR]. Not that my Linux would have booted after having it's partition "fixed." That is why I got the wonderful PM8.

Anyone else with experience of PartitionMagic out there. Hello again stewjack,
To try to answer you question more specifically, I finally found a link I was looking for that explains the situation very well if this link's information is correct.

[CENTER]             [HIW: **Partition Tables**]("http://www.ata-atapi.com/hiwtab.htm") 

[/CENTER]
[LEFT] The author of the document in this (above) link says,> The most important thing to    remember about partition tables is that there are no published    standards.  Also, in this section of the same link, [FONT=Arial][[COLOR=green]       PARTITION TABLE RULES[/COLOR]]("http://www.ata-atapi.com/hiwtab.htm#T3"),[/FONT]
[/LEFT]
> [FONT=Arial][COLOR=blue]PARTITION TABLE RULES[/COLOR][/FONT]  [FONT=Arial]Keep in mind that there are NO written rules and NO    industry standards on how FDISK should work but here are some    basic rules that seem to be followed by most versions of    FDISK:[/FONT]Kind of scary stuff eh? 
So it seems to me, if that page is up to date and that information is correct, that modern disk partitioning software is not all fully compatible with another brand or 'family' of disk partitioners. Each disk partitioning software developer or firm might have slight differences of opinion on some of the finer points, although they stick to the basic rules. 
So if you use one disk partitioning program, it might only be partially compatible with the work that another one has previously left behind in your partition table. Each disk partitioner would claim that theirs is correct and the other is faulty.  
Likely it isn't a case of being able to say one is better than another, or that one program is perfect and the other is 'buggy'.  
I think it's best to  choose one or the other and stick with the one you prefer, but be aware that the 'Parted based family of partitioners are all fully compatible with Linux. Other brands might not be so much.
If we switch brands of disk partitioners, it would be best to stick with the one we switch to, and not switch backwards and forwards.
I once decided to try out every brand of disk partitioner that I could get my hand on.  I finished up with a corrupt partition table and had to completely reformat the whole disk and begin again from scratch. It was only in a test computer, so I didn't lose any valuable data. Partition Magic was not one of the disk partitioners I tried out, so it has nothing to do with Partition Magic in my case.  Now I know there is [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), which I might have used to try to recover the table with if I had known about it at the time. [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is available on Live CDs or can be installed in Ubuntu through Synaptic Package Manager. But that's another subject...

Edit: ...and make sure you back up your data before working with disk partitioning programs.

Regards, Herman :D

---

### Post by bulldog on 2006-12-02
Thank you Herman,that's a reasonable explanation why things go wrong when you use different partition programs.
Will have a good look at the link you provided.

It explains to me why I often had trouble's when using PM8 in windows to create my Linux partitions.
I never had troubles with PM8 when I only resized windows disks or reformatted them.

---

### Post by stewjack on 2006-12-03
> **Herman said:**
> Hello again stewjack,
To try to answer you question more specifically, I finally found a link I was looking for that explains the situation very well if this link's information is correct.

[CENTER]             [HIW: **Partition Tables**]("http://www.ata-atapi.com/hiwtab.htm") 

Regards, Herman :D

Thanks for that link! I haven't had time to read it fully, but I promise you that I will read it fully.=D>

My next step is to post questions on the gParted forum. :idea: 
If anybody understands the specific incompatibilities, I should find them on that forum.  That may take me some time, but I haven't yet received my Dapper Drake CD, or my  Christmas present, a one GB USB stick.

The persistent install is my backup plan.

Jack 

If I learn anything I will be back

---

### Post by stewjack on 2006-12-08
> **stewjack said:**
> Thanks for that link! I haven't had time to read it fully, but I promise you that I will read it fully.=D>

My next step is to post questions on the gParted forum. :idea: 
If anybody understands the specific incompatibilities, I should find them on that forum.  

If I learn anything I will be back

I learned something specific - and short
[http://www.cgsecurity.org/wiki/Intel_Partition_Table]("http://www.cgsecurity.org/wiki/Intel_Partition_Table")

It may be that PM-7 tried to fixed the partitions, and possibly PM-8 just reports errors. If I ever get around to creating a FAT32 partition using gParted and PM-8 can't read it, then that could be the basic problem.

Jack

I just received Ubuntu 6.06 in the mail.:D

---

