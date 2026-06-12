---
title: "Dual boot same home?"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by Mascarade on 2013-01-19
Hi all!

I want to make a kubuntu install on a raid 0 and another distro like debian on a raid 0 too....i know how make the raid but...

My question is : Do i need to make a partition home for each of them?

If i put a /boot partition in kubuntu and a /swap and /  and /home, do i need to make just a / partition and a /swap partition in debian and used the /boot partition and /home partition for debian distro? 

Thanx for your response!! :p

):P

---

### Post by Ascurion on 2013-01-19
I can't help with the raid either, but I tried what you are aiming to do with two different Ubuntu versions. I have one home account and two "/" system partitions. I normally use this procedure when I upgrade to a new Ubuntu version to keep my running system around. in case I can't get all my mission critical software to run on the new version since Ubuntu is the system I use for work. 

However You have to be aware that all programs store their setup files in the home account in hidden folders. That means that if you boot two systems with one home account both systems will  start to configure these files. This may become a problem when you have different versions of software on the two systems. Therefore this dual boot setup may be not running very smooth in some cases and is maybe not a setup that can be recommended for stable operation. Such a configuration also may need a lot of maintenance. 

I only use this procedure  as a failsafe in case the new version does not work at all. 

In any case be sure to back up your home with all hidden files, before booting a different distribution with this home folder. 

As for setting up such a system I found two ways to install a second distribution and use your old home with it. One is to normally install a new system on one extra partition and then delete the home folder of this system and make a softlink ("ln -s") to your "real" home folder on the other partition/system. Or you create one partition with the home folder alone and a system partition for each distribution, and choose in the installation dialogue to use this already existing partition as your home folder. I tried both and they did work for me.

---

### Post by Cheesemill on 2013-01-19
You shouldn't use the same /boot or /home partitions for multiple distros. The only partition you can get away with sharing is swap.

I would use a separate root partition for each distro (without a separate home partition) and then shared swap and data partitions.

Make sure you install grub for your primary OS into the MBR of your hard drive, but to the distros root partition for your other OS(s).

---

### Post by ajgreeny on 2013-01-19
A slightly different way that I do it with my 5 different ubuntu family distros on one machine, is to have a separate /home partition for the main OS, in my case Lucid 10.04, and then leave the home folders of the other 4 OSs in their root partition, but make links to the data folders in Lucid (Documents, Downloads, Music, Videos, etc etc) to the home folders of the other OSs.  I also link the hidden .thunderbird and .mozilla folders, but if the OSs run different versions of FF or TB there can be extension problems to take care of.

That avoids most configuration problems from different versions of apps (see above re FF & TB), but removes the need for duplication of any data files.

---

### Post by oldfred on 2013-01-19
I am more like Cheesemill in that all my installs have /home inside / (root) and I use 25GB for / with about 8GB used. But all my data is in data partitions. One NTFS for data I used to share with Windows and one Linux format for all other data. And as ajgreeny does I link all my data folders back into /home.

I do not know RAID but have this info.
       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by Mascarade on 2013-01-31
Hey sorry for this long time response!!

Thanks a lot for all this precius information !!!

That work!!
:o)

---

