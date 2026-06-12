---
title: "Question Regarding Four Partitions Limit"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by livinlinkin on 2006-04-06
Please help me. I've recently come to loath Windows, and would really appreciate some aid on installing Ubuntu on my Dell 6000 laptop.

Because I only have one HD as of now, I need to create a dual boot system. Everything is going fine except the partitioning, which is a hassle. When I created my swap partition, the other free 5 GB was "unusable."

Here's my situation: (I'm a total n00b. Excuse my language, English.)

SCSI1 (0,0,0) (sda) - 60.0 GB ATA HTS548060M9AT0
#1 primary 65.8 MB :) fat16 /media/sda1
#2 primary 50.2 GB -> :) ntfs /media/sda2
pri/log 5.5 GB FREE SPACE
#3 primary 4.2 GB :) fat32 /media/sda3
pri/log 8.2 MB FREE SPACE

I plan on partitioning 5 GB for Ubuntu, and 500 MB as the swap partition. However, I can't since I can only have 4 partitions, I believe. My questions are as follows:

What's the purpose of the fat16 and fat32 partitions?

Why do I have two "chunks" of free space? Can I consolidate the two?

How do I circumvent the limit on partitions? Is it a limit on primary partitions only? 

How do I get around the "unusable" problem? Can I change/modify the other existing partitions safely; and if so, how?

Thanks in advance. The Ubuntu Live CD was an enlightening experience. :D

---

### Post by az on 2006-04-06
Well, you can only have four primary partitions.  You can end up with a lot more partition than that by using extended partitions.

You are trying to do the partitioning yourself?  The installer should be able to handle all that for you.

Just boot it and it will take care of everything.  It will ask you if you want ot use the free space and if you say yes, you will just have to confirm and go have a coffee while it creates your partitions and installs your Ubuntu system for you.

---

### Post by Phlosten on 2006-04-06
[QUOTE=livinlinkin]
I plan on partitioning 5 GB for Ubuntu, and 500 MB as the swap partition. However, I can't since I can only have 4 partitions, I believe. My questions are as follows:
What's the purpose of the fat16 and fat32 partitions?
Why do I have two "chunks" of free space? Can I consolidate the two?
How do I circumvent the limit on partitions? Is it a limit on primary partitions only? 
How do I get around the "unusable" problem? Can I change/modify the other existing partitions safely; and if so, how?
[/QUOTE]

1. fat16 and fat32 are old partition formats. fat16 is from the windows 95 and earlier days and fat32 usually came from windows98 and winME (god forbid you ever touched that), although winXP and Win2k are capable of producing fat32 partitions. The only drawback is that they have a filesize limit that is annoying (I think 4GB limit?).

2. No idea why you have 2 free chunks of space, but something created them that way. The easiest way to consolidate them would be to delete that third partition and recreate a new one using the total free space.

3. The limit on primaries is fixed, no way of getting around this as far as I know. However you get sidestep this by creating 'Extended' partitions within which more multiple logical partitions can live, as mentioned by azz.

4. There are tools to resize your existing partitions, but they do come with a risk, and personally I don't like that risk. The safest way is to backup everything you need from your windows installation and totally repartition your hard disk from scratch with either two configurations. 

<1> Create a single partition for Windows in NTFS format.
Then create a second partition in ext3 format for Ubuntu, and lastly a third partition for your swap file.  However with this method it is reported that it is not safe to actually 'write' to your NTFS parition from Linux. (Although some people are doing it).

<2> Same as above but with a fourth parition in Fat32 format that both Linux and Windows XP/2k can write to safely. Kind of a half way point to share data.

---

### Post by Herman on 2006-04-06
>  SCSI1 (0,0,0) (sda) - 60.0 GB ATA HTS548060M9AT0
#1 primary 65.8 MB :smile: fat16 /media/sda1
#2 primary 50.2 GB -> :smile: ntfs /media/sda2
pri/log 5.5 GB FREE SPACE
#3 primary 4.2 GB :smile: fat32 /media/sda3
pri/log 8.2 MB FREE SPACE
If this was mine I would use Gparted livecd and slide the #3 primary over to the end of #2 so I would have no free space between them and 13.7 GB free at the end of my disk to install Ubuntu on.
 Then I'd do as azz said and install Ubuntu with  Ubuntu installer's partitioner. 

Pholsten is right too.
I would like to add something though, there is a small amount of risk involved in partitioning the same as everything we do. It is not good to go through life being scared of everything though. Risks can be managed, and as long as you are prepared for what can be foreseen to go wrong (back up your data), there is nothing to fear. It's a lot more work to back up Windows properly and re-install compared with Ubuntu, but on the other hand, it does Windows a lot of good to be re-installed frequently, it gets rid of all the spyware and malware if you do it right and don't put them back in again.

" A ship in the harbour is safe, but that is not what ships are made for."

---

