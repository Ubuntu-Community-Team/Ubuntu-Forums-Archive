---
title: "installing on already partitioned drive"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by spencerownside on 2011-01-12
i am new to ubuntu and have been happy with most of my experiences so far. i have already converted several comps and would like to switch my main media comp over to ubuntu (away from vista). i have gone through the installation tutorials, wiped other hard-drives and successfully installed and begun running ubuntu elsewhere, and read through and looked at the screen-shots; so i feel pretty comfortable. 
however, i just want to double-check. 
my media comp is on vista. it has a partitioned drive; it is in total 750g, with 100g basically as the main drive- or "C". and the rest, the storage stuff is partitioned off into a "D" drive. the "C" & "D" drives are on the same physical drive- just the partition separates them. 
i am just afraid to lose my media stuff: music and the such. it would really suck to lose all that. i am so close to freeing myself from microsoft but before i screw up the big hard-drive i was just hoping there is someone out there who has done this type of thing before and could assure me that the screen-shots that show this option are really there. 
muchos gracias

---

### Post by sikander3786 on 2011-01-12
Welcome to the forums :-)

First of all, you need to be careful. I have done that stuff lots of time and never messed up any thing but remember, strong backup is the right path to proceed.

Secondly, you need to delete your C: drive and create at least 2 partitions in its place. 1 '/' Ubuntu System Partition and 2 'Swap' Partition.

But, before doing any thing else, I would suggest to boot an Ubuntu Live CD/USB and post the output of this command from Applications > Accessories > Terminal.

```
sudo fdisk -lu
```

We need to see how many partitions are there, how many Primary or Extended/Logical before advising any thing. And that output will help us know more about your setup ;-)

---

### Post by Rubi1200 on 2011-01-12
Hi and welcome to the forums :)

First, boot the computer with a LiveCD, choosing to try not install.

This way you can check whether the current version works with all your hardware.

Next, at the live desktop go to Applications > Accessories > Terminal and run this command:

```
sudo parted -l

```
(lowercase L not 1)

Copy/paste the output and post it here so we can see what the drive looks like.

Finally, if you decide to install 10.10, use the manual partitioning option only. There are known issues with the other options and the install alongside option could quite likely destroy the Windows install.

We will be more than happy to advise you on the best options, but please post the results of the command first.

Thanks.

---

### Post by spencerownside on 2011-01-12
this maybe a stupid question and i apologize ahead of time- is this "live cd" a special cd? 
the boot disc that i have been using for my other comps (the specific disc that i used to set up the now ubuntu run comps) is just the cd that i burned for the official ubuntu provided .iso file onto. 
i am sorry i didn't type that very clearly- i just woke up.
i guess i am just asking if the same disc i have been using will work for this or if there is a special specific disc that is the "live cd"?
gracias for help- appreciate it.
also, ahead of time, there are two different command lines posted- a different one for each reply: any idea as to which one i should use?

---

### Post by sikander3786 on 2011-01-12
Any Ubuntu Desktop Disc is a Live CD which has a "Try" mode.

As far as the commands are concerned, any of them might be equally helpful.

---

### Post by spencerownside on 2011-01-12
muchos gracias. i figured as much (minus the command info); i would just hate to lose the info and since this is my first install in which it actually matters that i do it correctly, i just wanted to be safe. thank you.

---

### Post by spencerownside on 2011-01-12
muchos gracias. i figured as much (minus the command info); i would just  hate to lose the info and since this is my first install in which it  actually matters that i do it correctly, i just wanted to be safe. thank  you.

---

### Post by spencerownside on 2011-01-12
muchos gracias. i figured as much (minus the command info); i would just  hate to lose the info and since this is my first install in which it  actually matters that i do it correctly, i just wanted to be safe. thank  you.

---

### Post by spencerownside on 2011-01-17
i am in the process of installing onto my drive: but i have gotten to a point where i am being allowed to do the partitioning and i am not sure what to do from here. i see my 2 existing partitions: sda1 & sda2. 
#2 is the one i am trying to keep- so i have selected #1, am in the 'change' menu there multiple 'edit' options. some of them are 'ext3 journaling file system', a couple other 'journaling file system'; and then 'fat16' & 'fat32'. i am pretty sure i am supposed to choose fat32.
i think i should select my #2 drive and make sure it's edit settings are on 'do not use the partition' option. 
does this sound correct by chance?

---

### Post by spencerownside on 2011-01-17
and i guess the real problem is that i am not sure about the error i am getting. in the boot loader drop-down, i have Partition #1 selected (the other choices are the whole drive [ /dev/sda ATA WDC wd7500aaks-0 ] and /dev/sda2), click 'install now' and i get an error "no root file system is defined. plese correct this from the partitioning menu"
not quite sure what i have wrong and would rather ask than screw this up. graci

---

### Post by Quackers on 2011-01-18
Grub is normally installed to the mbr of the drive - in your case sda - not a partition like sda1.
The root system not specified means that you have not selected / as the mount point for your root partition.
I see that you are using sda1 as your Ubuntu partition. Is this in an attempt to over-write Vista? The default file system type is now ext4 for the main Ubuntu partition.

---

### Post by spencerownside on 2011-01-18
thank you for the 'ext4' info. yes i am trying to "overwrite" vista. I'd put it in terms that are much less diplomatic, but basically -- yes, i would like to never see vista on my pc again. i want to keep sda2, because that is my storage drive. that's where i have my music and some of those files would be tough to replace.
i confess, i don't really understand much of your first 2 sentences- and not in that you said it poorly, but in that i am pretty new at learning the actual jargon of these processes. i don't know what 'grub' or 'root mount point', or 'root system' really mean. i am becoming more familiar with the words, but what they all are and what they all do is still new to me. 
thank you again for help and patience

---

### Post by Quackers on 2011-01-18
Grub is the bootloader that loads Ubuntu. It is installed to the beginning of the hard drive, not to a partition, as such. In your case you should choose sda instead of sda1, as you previously reported.
Your root partition (unless you have chosen to have a separate /home partition) is your main Ubuntu partition. In the partitioning stage of the installer you need to choose its size (which in your case should be the size of your C: partition), its type, which is chosen via the drop-down menu - where it probably said "do not use this partiton" originally, which is ext4, the mount point, which is " / " for /root, and tick the box to select "format"

---

### Post by spencerownside on 2011-01-18
so i did what you suggested and it seemed to work, but when i do the install it gives me a choice about a "swap space". i am down with making a suggested space but when i went back and tried to make a new partition i think i must have had something clicked wrong because i almost scratched the whole harddrive. i'd like to just make a 5-10 gig swap space out the main sda1/"C" drive. 
any more suggestions por favor?

---

### Post by Quackers on 2011-01-18
How much ram do you have? Do you intend on using the hibernate function (if it works). If you have 2GB or more of ram, and don't intend on using hibernate, you can almost certainly do without a swap partition.

---

### Post by spencerownside on 2011-01-18
i am pretty sure that i have 2 gigs of ram. i also will probably at some time be doing some video & audio editing stuff. i am just doing the install- i assume i can add a 'swap section' later; and if not, i will be able to just re-do the C again... no biggie. 
how would i go about setting up the 'swap space' either post install; of if/do i have to re-install?
gracias for the help

---

### Post by Quackers on 2011-01-18
During the partitioning stage you would make your ext4 partition a few GB smaller and then create a new partition of that size for swap.

---

