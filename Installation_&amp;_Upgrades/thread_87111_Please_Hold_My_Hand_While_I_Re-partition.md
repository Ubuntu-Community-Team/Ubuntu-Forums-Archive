---
title: "Please Hold My Hand While I Re-partition"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by Ubuntist on 2005-11-07
I'm a noob trying to install Breezy on a Dell 8300 with a single 160-GB hard drive.  I'd like to dual boot with my existing XP installation.  And I'd really like to preserve XP and all XP data, although I have backed all the data up.

Currently I have a 60-GB primary NTFS partition on which XP resides; about 20 GB of that partition is actually in use, including 5 GB of my own data.  Three ext3 partitions exist for the Mandriva installation that I want to replace, but there is no Mandriva data that I need to preserve.

When I get to the partitioning phase of the installation, I start to get scared.  Specific questions:

1.  I'm thinking of having separate / and /home file systems.  Is this a good idea?  About how big does / need to be?

2.  Would there be any advantages to having even more separate file systems, e.g., /sys or /usr?

3.  Is there any advantage to having more than 512 MB of swap space?  If it matters, I have 512 MB of RAM.

4.  To facilitate exchanging data between Ubuntu and XP, I'm thinking of devoting a couple of gigabytes to FAT32 partition.  Does that make sense?  Would it be better to try to reformat the whole XP partition under FAT32?

5.  Is ext3 the best format to use for the Ubuntu partitions?

6.  Am I correct in assuming that all of the new partitions I create for Ubuntu should be logical rather than primary?

Any wisdom would be much appreciated.

Your trembling novice,

  Ubuntist

---

### Post by markr on 2005-11-07
Plenty of questions!!  I'm no expert, but I can give you the benefit of my experience installing a number of linux distros:

1. Seperate / and /home partitions makes it easier to reinstall.  You can erase / without loosing your own data in /home.  Personally I only create one big / partition, but have a separate partition with all my data in so I can share between linux and windows.

2. You'll find a number of articles on the web about different partitions for different areans (I think /usr, /home and / are popular ones). As a noobie, I'd be tempted to create one big partition and see how you go.

3. I have 1gb memory and a 1 gb swap.  So far Linux has not even touched the swap space.  I think you are okay setting it up as 1xmain memory.

4. FAT32 is a good way of sharing data.  Another option is a program called something like IFS (can't remember exactly what it's called).  This is installed on windows and allows windows to read/write ext2/3 partitions as if they were native Windows partitions.  I have a 15 gig ext3 partition to share data between windows and linux.

5. I think ext3 is pretty much the standard and a good default.  ReiserFS is a newer type,  but I think it is not the standard at the moment (not sure what advantages it gives you).

6. You can only have 4 primary partitions,  if you want more partitions you will have to create logical ones,  I don't think Linux cares what type it is.

Hopefully,  someone with more experience will also apply.  This is just from my experience.

Mark.

ps.  Always backup anything you don't want to lose !!!!

---

### Post by earobinson on 2005-11-07
1. The only realy advantage to this is that if you boot 2 versions of ubuntu, or ubuntu and debian you can use the same home for both. Also if you are going to reformat a lot and dont want to loose all your settings this is a good idea. how big is up to you. by default ubuntu trys to save everything to your home dir, but i assume that you would be saving everything to you fat32 partition since u want to shair between windows and ubuntu. So i would say at least 1 gig but you probaly only need half that (will check my home dir size when i get home if you want)

2. not really unless you are doing some complacated dual booting of dif versions of linux

3. all depends on what you will be doing in ubuntu, swap is like virtual memory in windows. I think the normal settings for ubuntu is 1 gig swap.

4. This is the best idea and what i did when i was switching from windows to ubuntu, make a partition named 'data' and keep all your data that you want ubuntu and windows to use on it.

5. [http://en.wikipedia.org/wiki/Ext3#Disadvantages](http://en.wikipedia.org/wiki/Ext3#Disadvantages)

6. [http://ubuntuforums.org/showthread.php?t=35587](http://ubuntuforums.org/showthread.php?t=35587)

Great Question! hope this helps

(dam i was to slow, this happens more and more)

---

### Post by lorenco on 2005-11-07
> **Ubuntist]I'm a noob trying to install Breezy on a Dell 8300 with a single 160-GB hard drive.  I'd like to dual boot with my existing XP installation.  And I'd really like to preserve XP and all XP data, although I have backed all the data up.[/QUOTE]

You may "safely" use parted to resize a FAT32 Partition.  (Can't remember if windose can convert NTFS to FAT32, but seems to think not :( )  I have resized a fat32 partition without losing any data.

[QUOTE=Ubuntist]
1.  I'm thinking of having separate / and /home file systems.  Is this a good idea?  About how big does / need to be?
[/QUOTE]
It is always not a bad idea to have /home /boot and /usr split off although I never do that caus it is too much admin and filesystems to keep track of. I'd rather keep / huge and make a backup of /home and /etc if I need to migrate / re-install.

This is not good for server and multi user environments but good enough for a desktop.
[QUOTE=Ubuntist]
2.  Would there be any advantages to having even more separate file systems, e.g., /sys or /usr?
[/QUOTE]
Yes: More Admin  said:**
> 
3.  Is there any advantage to having more than 512 MB of swap space?  If it matters, I have 512 MB of RAM.

Best Practise is SWAP = RAM to SWAP = RAM * 1.5
You do not really want to use more swap mentioned above, rather buy more ram (it's cheap lately)
[QUOTE=Ubuntist]
4.  To facilitate exchanging data between Ubuntu and XP, I'm thinking of devoting a couple of gigabytes to FAT32 partition.  Does that make sense?  Would it be better to try to reformat the whole XP partition under FAT32?
[/QUOTE]
I normally do the following that helps easy the pain of multiple disks shared (Like I have VMWARE shareing a data disk with Linux.

I create a BIG FAT32 Partition to store all my docs / userfiles I want to share with Linux / VMware / Win (if I have it on the PC).
I then have 1x Windows System (If, yet again i have it) 1-2x Linux roots. 1x /boot 1x swap This works for me...


[QUOTE=Ubuntist]
5.  Is ext3 the best format to use for the Ubuntu partitions?
[/QUOTE]

I prefer reiser ... it's a better all round File System

[QUOTE=Ubuntist]
6.  Am I correct in assuming that all of the new partitions I create for Ubuntu should be logical rather than primary?
[/QUOTE]

Nope, does really not make any diffs... Depends on you setup (you r limitied to 4 Primary Partitions per hdd. So only use Logical if you exceed 4 partitions...
(One more reason i do not have windows on my laptop any more ... :smile:

---

### Post by Ubuntist on 2005-11-08
Thanks very much, everybody.  I was able to install without much difficulty.  I went with separate partitions for / and /home, allocating about 40 GB to / (probably too much, but I'm not using much of the disk anyway).  I decided to use the Reiser file system except for the partition to be used for sharing files with Windows, which is FAT32, of course.

Now I'm having a few miscellaneous problems getting things set up exactly like I want them, but it's nothing too scary (so far!).

I really do like Ubuntu much better than Mandriva.  It feels more solid and the updating system is far superior to Mandriva's.  The only thing I miss is being able to choose different desktop environments, as I've not yet decided which one I prefer (GNOME, KDE, etc.).

Thanks again!

---

### Post by markr on 2005-11-08
If you've installed Ubuntu you can install the kde desktop using the updates easily enough.  That way you will have Gnome and KDE to play about with

---

### Post by Ubuntist on 2005-11-08
[QUOTE=markr]....  That way you will have Gnome and KDE to play about with[/QUOTE]

Cool!  I thought that once I installed KDE I'd lose Gnome.  I'll give it a try....

---

### Post by earobinson on 2005-11-08
nope you can install many desktop environments installed for the same distro.

---

### Post by rpimn on 2005-11-08
Hello everybody,

I have the same problem as Ubuntist had.
I am quite nervous for the partition section.
I have 160 GB HD as master (the first hard drive) and another 160 GB HD as slave (the second hard drive).
I already saved all my data in the second hard drive, and intend to replace my Redhat 9 (in the first hard drive) with Breezy Badger.

Could you please share your experience with me about your installation experience.
In particular, do I need to unplug the IDE cable which is connected to my second hard drive, to ensure that I will not loose my data. 
Or Ubuntu will erase all the existing partition in the first hard drive only ?

Any help and suggestions would be greatly appreciated.
Thanks.

---

### Post by Ubuntist on 2005-11-08
rpimn, I'm obviiously no expert, but the Ubuntu installer will offer you several options for partitioning, including a manual option that allows you to select which partitions you want to change or delete.  I think your data will be perfectly safe if you go for the manual option, and I do not believe there is any need to unplug the IDE cable.  In the worst case, you still have the option to bail out and reconsider.

---

### Post by earobinson on 2005-11-08
I unplug whe Im installing a rc (release candidate) but then i had a bad expirence with fc.

but ubuntist is right, shouldent have to just check that its not doing anything to hdb. But better safe than sorry is always good 2.

---

### Post by rpimn on 2005-11-09
Ubuntist, thanks a lot for your tips. I am quite relief to hear this good news.
Many thanks  !

---

