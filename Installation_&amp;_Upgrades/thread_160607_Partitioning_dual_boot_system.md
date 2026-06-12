---
title: "Partitioning dual boot system"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by swawryk on 2006-04-15
Hi all,

Does anyone have any recommendations about how to partition my HDD for a dual boot system?

How about something like:

1. Windows system and programs
2. User data (shared by Windows and linux)
3. Linux sustem and programs
4. Linux swap partition

The system is a notebook and the HDD is 80GB.  Thanks for any suggestions.

:-k 
Steve

---

### Post by frodon on 2006-04-15
I would do that : 
1- 10Go NTFS windows
2- 10Go ext3 linux system
3- swap 1Go if you have 1Go RAM
4- 19Go FAT32 user data partion (work in both OS)
5- 40Go ext3 user date partition (read only under windows)

It's a good solution for someone who is used to windows and want to use ubuntu as primary OS.

---

### Post by johso on 2006-04-15
I can tell you what I always do (With my 60Gb harddisk):

I always place the Windows paritition (10Gb) as the first on the harddisk, since I've experienced weird problems with Windows (when it isn't the first thing on the disk). I also got this verified by others having the same problem.
Then I create my Ubuntu partition, which I gave 8Gb this time, and then did the automatic partitioning thing from the Ubuntu installer.
And at last it's time for my FAT32 partition which is for everything shared between Windows and Ubuntu - which is about 40Gb.

Thing is - don't give your OS partitions to much space. I always end up regretting this, since it could have been used otherwise, and isn't used for anything.

---

### Post by bscbrit on 2006-04-15
This is quite a common configuration.  I will not specify sizes for the partitions - it depends on how much data you have and how you will be accessing it.

My suggestion is (and it is only 1 of millions of possibilities)

/hda1 NTFS windows XP

/hda2 Extended Partition - not directly mountable but holds the following partitions:

/hda3 FAT32 shared partition
/hda4 Linux /
/hda5 swap
   and perhaps
/hda6 home

Just one possibility.  The swap partition should be about twice your amount of RAM but no bigger than 512MB.  In these days of GBs of RAM I don't suppose the swap partition is as important as it once was but we can all spare enough space to have a good size swap e.g. 512MB or, if you really don't care, 1GB but the former is more than adequate.  No-one should be swapping GBs of RAM to and from disk!

---

### Post by johso on 2006-04-15
[QUOTE=frodon]I would do that : 
1- 10Go NTFS windows
2- 10Go ext3 linux system
**3- swap 1Go if you have 1Go RAM**
4- 19Go FAT32 user data partion (work in both OS)
5- 40Go ext3 user date partition (read only under windows)

It's a good solution for someone who is used to windows and want to use ubuntu as primary OS.[/QUOTE]

Now, I don't know much about the swap partition other than it's used for... well, swapping files. But I do have 1Gb of RAM, so I should actually have a 1Gb swap partition?

---

### Post by frodon on 2006-04-15
If i remember well you can choose the swap size only if you perform an installation in expert mode, by default the install process will set the same swap size than your RAM size.
When your system is running the RAM is used to store some datas needed for the apps you're running but not all of these datas are really important (on the speed level) therefore apps datas which not require hard speed constraint will be store in the swap (it's on your hdd so it's slower than a RAM memory).
If you have, like me, an old computer the swap will also be used if the whole RAM memory is full.

johso, don't bother with swap size, let the install process set it, same swap size than the RAM size is a common setting and fits the need of most users, so really don't bother ;)

---

### Post by johso on 2006-04-15
Okay, I won't then. ;-)

---

### Post by swawryk on 2006-04-17
[QUOTE=bscbrit]My suggestion is (and it is only 1 of millions of possibilities)

/hda1 NTFS windows XP

/hda2 Extended Partition - not directly mountable but holds the following partitions:

/hda3 FAT32 shared partition
/hda4 Linux /
/hda5 swap
   and perhaps
/hda6 home[/QUOTE]

[QUOTE=frodon]I would do that : 
1- 10Go NTFS windows
2- 10Go ext3 linux system
3- swap 1Go if you have 1Go RAM
4- 19Go FAT32 user data partion (work in both OS)
5- 40Go ext3 user date partition (read only under windows)[/QUOTE]

Thanks to all of you.  This gives me a good idea of what to do.  It seems 5 partitions with 1 being a small swap partion is a good way to go.

I think I will make the Windows a bit bigger than 10GB though because it's already nearly 10GB and I want room for more stuff on it yet.

Thanks again,
Steve
:)

---

### Post by Pettman on 2006-04-17
[QUOTE=frodon]If i remember well you can choose the swap size only if you perform an installation in expert mode, by default the install process will set the same swap size than your RAM size.[/QUOTE]It is determined when you partition your hard drive, and if you are setting up the system for dual boot you are likely to use of the manual partitioning any way.
If you have 1 GB of RAM (I have) you can probably do with out any swap at all (I have none and have never run out of memory).
Addition: I'd also recomend to put the /home dir on a separate partition (it makes re-installing the system a lot easier).

---

