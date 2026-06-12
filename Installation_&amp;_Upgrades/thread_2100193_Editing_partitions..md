---
title: "Editing partitions."
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-12-31
Hello; I have gone to a dual boot {again} on one of my laptops, ubuntu 12.04 & win. 7.
I couldn't seem to find the options i wanted regarding partitioning so i installed
alongside windows 7 to the unallocated space i had arranged prior.
     I wanted to try a separate home  for ubuntu, but wanted some advice before i
start editing, or would it be better to have a separate data nfts partition, accessible from both OS ?
       It's not really imperative to do this but again i am experimenting, i really want to be
able to learn and manage the whole installation, partitioning and booting principles.
    Please feel free to offer advice, and thank you. 
Screen shot attached.

---

### Post by 2F4U on 2013-01-01
A seperate home partition on Ubuntu should only be used from Ubuntu. It is not advisable to access it from other operating systems due to the risk of data corruption, since the home folder also has configuration information in it.
A seperate data partition is what I would recommend, if you intend to access your data from within different operating systems. The home folder on Ubuntu could then, for example, stay inside the only partition and would contain only the individual configurations of your applications. The data would reside on the shared partition. NTFS would be a good choice if the partition is accessed from both Windows and Ubuntu.

---

### Post by ibjsb4 on 2013-01-01
On data partitions

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by offgridguy on 2013-01-01
> **ibjsb4 said:**
> On data partitions

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en)
This link doesn't seem to do anything.

---

### Post by offgridguy on 2013-01-01
> **2F4U said:**
> A seperate home partition on Ubuntu should only be used from Ubuntu. It is not advisable to access it from other operating systems due to the risk of data corruption, since the home folder also has configuration information in it.
A seperate data partition is what I would recommend, if you intend to access your data from within different operating systems. The home folder on Ubuntu could then, for example, stay inside the only partition and would contain only the individual configurations of your applications. The data would reside on the shared partition. NTFS would be a good choice if the partition is accessed from both Windows and Ubuntu.
Thanks for the reply, for a seperate data partition, what would you suggest size wise ? Also what do you suggest as a mount point?  Since i have never used a data partition, is there a required procedure to write to and retrieve from ?

The explanation of the home folder having configuration info is especially
helpful.:)
Thanks again

---

### Post by ibjsb4 on 2013-01-01
> **offgridguy said:**
> This link doesn't seem to do anything.

Firewall ?

---

### Post by 2F4U on 2013-01-01
> Thanks for the reply, for a seperate data partition, what would you suggest size wise ? 

This entirely depends on what you have available and what you intend to store on the partition. If it is just "normal" documents, 50 GB may be sufficient, but if it is for pictures, videos or other "heavy" stuff, you will likely need more.

> Also what do you suggest as a mount point?  Since i have never used a  data partition, is there a required procedure to write to and retrieve  from ?

You can name the mount point anything you like. For example, I have 3 partitions on and have named them /u01, /u02, and /u03. They are automatically mounted and show up under the root filesystem (through entries in /etc/fstab), but it can also be that you don't like automounting.

> The explanation of the home folder having configuration info is especially
helpful.

This information is usually stored in hidden folders such as .config, .local or in a hidden folder named after the application.

---

### Post by oldfred on 2013-01-01
See post #2 in this thread. :)

[http://ubuntuforums.org/showthread.php?t=2096414](http://ubuntuforums.org/showthread.php?t=2096414)

---

### Post by offgridguy on 2013-01-01
> **2F4U said:**
> This entirely depends on what you have available and what you intend to store on the partition. If it is just "normal" documents, 50 GB may be sufficient, but if it is for pictures, videos or other "heavy" stuff, you will likely need more.



You can name the mount point anything you like. For example, I have 3 partitions on and have named them /u01, /u02, and /u03. They are automatically mounted and show up under the root filesystem (through entries in /etc/fstab), but it can also be that you don't like automounting.



This information is usually stored in hidden folders such as .config, .local or in a hidden folder named after the application.
Nothing heavier than pictures, 50 GB sounds good.
I have nothing against automounting, just want to be sure i can find my
stuff :D .

---

### Post by offgridguy on 2013-01-01
> **oldfred said:**
> See post #2 in this thread. :)

[http://ubuntuforums.org/showthread.php?t=2096414](http://ubuntuforums.org/showthread.php?t=2096414)

Thank's oldfred, how embarrassing , my own thread.  I realize it would be better to have
this set up prior to install, but now that  the install is complete is there anything i should
be aware of when editing" after the fact" ?

---

### Post by offgridguy on 2013-01-01
> **ibjsb4 said:**
> Firewall ?
Very possible, this ubuntu version has the dansguardian web content filter.

---

### Post by oldfred on 2013-01-01
Moving partitions around is like the old slide puzzle game. Sometimes you have to move a lot of pieces just to make one piece move the right place. I do not like moving partitions left as then you are copying all your data. Best to have good backups, but then backups are always a good idea.

I still have two data partitions, I started with a 20GB FAT32 for sharing with XP and then when I got a new drive converted to 100GB NTFS and anther 100GB ext3 ( I would use ext4 now). I have stopped using XP but still have Firefox & Thunderbird & all photos  (Windows Picasa in wine) in the NTFS partition as those applications were the same in both systems. All new data now goes into my Linux data partition.

The only data not in /home is .wine for Picasa. Photos are in shared but it is more difficult to move .wine as I understand it. So my /home is about 2GB with over 1.5GB the .wine. The user settings are actually pretty small. So I now keep /home inside my / (root) and just have data partitions.

Very new users are fine with just / & swap. But we usually suggest adding a separate /home to keep system from data. But then as you advance, separate data partitions may make more sense. The separate data partitions are more for dual booting and then sharing data.

---

### Post by offgridguy on 2013-01-01
Thank you oldfred for the very good explanation. :D

---

