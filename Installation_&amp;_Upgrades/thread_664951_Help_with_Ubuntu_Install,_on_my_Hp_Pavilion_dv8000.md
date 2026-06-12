---
title: "Help with Ubuntu Install, on my Hp Pavilion dv8000 Laptop"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by Manny.A on 2008-01-11
Help with Ubuntu Install, on my Hp Pavilion dv8000 Laptop

Model: HP dv8000
Operating System: Windows XP PRO with Service Pack 2
Processor: Intel Centrino Duo T2600 @ 2.16GHz
2.16GHz, 2.00 GB of RAM
Wireless Card: Intel(R) PRO/Wireless 3945ABG Network Connection 
Graphics Card: Nvidia geForce Go 7400
Video BIOS Version: 5.7222.41.89
Ubuntu (Version): 7.10
Kernel Options: None

Hi All:

I am a new to Ubuntu, and I am thinking of installing Ubuntu on my Hp Pavilion dv8000 Laptop Computer. I plan on putting Ubuntu on my D: drive, it has NTFS 101GB of free space on it I plan to allocate 50GB to Ubuntu. The other half of the drive has some data files and some programs on it.   

I have Partition Magic to setup the Partitions. Is it best to set up the root Partition and home Partition, and swop Partition. My self or let LINUX do it for me, when I install LINUX to the 50GB Partition.

I need some help in this mater, that will not heart my computer. 

Thank you in advance,

Manny

---

### Post by thenailedone on 2008-01-11
Hi... you can create a 15-20gig partition for /, a 2gig partition for swap and the rest for /home... you can use partition magic to do it before installing Ubuntu or let Ubuntu create them when installing (I have never had problems) but like any good guide would suggest: "Make backups!"  There is always a possibility of loosing data when creating/editing partitions...

I have to confess that I have not installed a distro of GNU/Linux on a drive that didn't already have my Windows install on it and I am not sure how the GRUB loader (that lets you choose between booting Windows or Linux) handles this (I will do a search or two and come back to you, time permitting)...

Good luck :)

---

### Post by mikewhatever on 2008-01-11
Check out the link --> [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by Manny.A on 2008-01-11
:)

Thank You thenailedone

This seems like I good plan. I will set up the partitions as you sagest, it pretty close
To what I have read in Running Linux book I will what for your new response on installing Linux on a drive that didn't already have my Windows install on it.

And thank you mikewhatever for the grate link [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Thank you for your fast response I can’t what to install Ubuntu, But all things in time.

---

### Post by thenailedone on 2008-01-11
This from [http://psychocats.net/ubuntu/partitioning:](http://psychocats.net/ubuntu/partitioning:)

> Sometimes people have two physically separate hard drives. You should treat that the same as having two pre-defined partitions. The same principles apply. You can have one hard drive be Windows, the other be Ubuntu. You can partition the first drive to be Windows and Ubuntu and then make the second drive a place to store shared data.

Seems that the best way is to put Windows and Ubuntu on the same physical harddrive and rather use the second to store data... if it is NTFS or FAT32 then both Ubuntu and Windows can read and write to it...

Also from [http://psychocats.net/ubuntu/partitioning:](http://psychocats.net/ubuntu/partitioning:)

> Some Windows users have a program called Partition Magic, but many Ubuntu users have reported problems with setting up a dual boot after using Partition Magic. It's better to use one of these partitioning tools instead (and they're all cost-free). Here are some: QTParted - available on Knoppix live CDs. GParted - available as the default partitioning program for Ubuntu's Desktop CD. DiskDrake - available on PCLinuxOS's live/installer CD.

...so, watch out for Partition Magic :)

---

### Post by Manny.A on 2008-01-12
:)

Thank you, thenailedone

I have ban reading some of the outstanding information that your links
Have provided to me. I am imprested at the wealth of information that there is 
To read and understand. 

[http://psychocats.net/ubuntu/partitioning:](http://psychocats.net/ubuntu/partitioning:)

[http://psychocats.net/ubuntu/partitioning:](http://psychocats.net/ubuntu/partitioning:)

But at the same time the information is lade out is such a manner that it is 
Easy for me to understand and implement thank you.

As for the partitions, you sagest that I put a ( 15 – 20 Gig / Root ) partition on 
My C: drive Ok I can do that. What do you thank about putting the 2 Gig Swap partition,
And / home partition on the D: drive.

Thank you,

---

### Post by thenailedone on 2008-01-12
Cool plan!

(BTW the reason for a 2gig swap partition is that it is all you will need when you hibernate Ubuntu (as you have 2 gig RAM and it basically dumps the RAM to the partition so when you start up again everything is like it was when you hibernated (all open apps etc. are still open and it looks like you never put of the PC))...


Good luck and keep us posted on you r progress...

---

### Post by Manny.A on 2008-01-13
[FONT="Comic Sans MS"]This is cool :)

But at the same time I am nerves about it. Witch is a good thing I have perched 
A book called, A Practical Guide to Ubuntu Linux by Mark G. Sobell. Have you read? 
This book, In Chapter 2 it covers the installation overview and walks you throw the installation
Step &#8211; by &#8211; step. I will be installing Ubuntu 7.10 some time today.

I will keep you posted on my progress      
[/FONT]

---

### Post by Jake90 on 2008-01-14
> **Manny.A said:**
> [FONT="Comic Sans MS"]This is cool :)

But at the same time I am nerves about it. Witch is a good thing I have perched 
A book called, A Practical Guide to Ubuntu Linux by Mark G. Sobell. Have you read? 
This book, In Chapter 2 it covers the installation overview and walks you throw the installation
Step – by – step. I will be installing Ubuntu 7.10 some time today.

I will keep you posted on my progress      
[/FONT]

WAIT. Before you install gutsy (Ubuntu 7.10) read this[http://ubuntuforums.org/showthread.php?t=582220]("http://ubuntuforums.org/showthread.php?t=582220")
Gutsy is terrible for HP laptops, In this case the older version is better. I down loaded Gutsy and I had to uninstall it. Right now I am in the process of installing Feisty.

---

### Post by Manny.A on 2008-01-14
[FONT="Comic Sans MS"]

:lolflag:

Will that did not work at all. I tried to install from the DVD with 
No luck and the live install.

Every thing was fine up to the point of preparing the dick space:
I used the guided-resize partition, set it to 28% ( 30.4 GB )
Then write changes to disk.

And then Migrate Documents and settings: went thru that step to the
End of it and the program crashes “unbiqulty” closed.

Then tried the live install, from the desktop no good

Time to do a recovery


[/FONT]

---

### Post by Manny.A on 2008-01-14
> **Jake90 said:**
> WAIT. Before you install gutsy (Ubuntu 7.10) read this[http://ubuntuforums.org/showthread.php?t=582220]("http://ubuntuforums.org/showthread.php?t=582220")
Gutsy is terrible for HP laptops, In this case the older version is better. I down loaded Gutsy and I had to uninstall it. Right now I am in the process of installing Feisty.


:confused:


Just a little late for me, but I will look in to it thank you

---

### Post by Manny.A on 2008-01-14
> **Jake90 said:**
> WAIT. Before you install gutsy (Ubuntu 7.10) read this[http://ubuntuforums.org/showthread.php?t=582220]("http://ubuntuforums.org/showthread.php?t=582220")
Gutsy is terrible for HP laptops, In this case the older version is better. I down loaded Gutsy and I had to uninstall it. Right now I am in the process of installing Feisty.

:confused:

Just a little late for me, but I will look in to it thank you

---

### Post by Manny.A on 2008-01-15
> **Manny.A said:**
> :confused:

Just a little late for me, but I will look in to it thank you

:)

Thank God, for Norton Ghost. I perched this product in November 2007 and 
Burned an image of my hard drives on my laptop to an external hard drive
As well as three DVD’s the DVD’s did not work. 

But the image I Burned to the external hard drive worked like a charm I have heard
Talk about Ghost but I am happy with it. 

I don’t under stand what happened to the DVD’s I wonder if Ubuntu 7.10 had some
Thing to do with it, I will have to look in to it.

I am just about done tweaking my system, and then I will Burn a new 
Image to my external hard drive, and try Ubuntu 7.04 I am determined 
To get it to work some how.  


:lolflag:

I Just love This stuff.

---

### Post by Jake90 on 2008-01-15
> **Manny.A said:**
> :)

Thank God, for Norton Ghost. I perched this product in November 2007 and 
Burned an image of my hard drives on my laptop to an external hard drive
As well as three DVD’s the DVD’s did not work. 

But the image I Burned to the external hard drive worked like a charm I have heard
Talk about Ghost but I am happy with it. 

I don’t under stand what happened to the DVD’s I wonder if Ubuntu 7.10 had some
Thing to do with it, I will have to look in to it.

I am just about done tweaking my system, and then I will Burn a new 
Image to my external hard drive, and try Ubuntu 7.04 I am determined 
To get it to work some how.  


:lolflag:



I Just love This stuff.

Great!!! I had a lot of problems with gutsy, but now that I switched to feisty (7.04) I love linux. Keep going at it and make it work it's worth it.

---

### Post by pcmann2004 on 2008-04-02
hello,
i just installed ubuntu 7.10

my setup
dv8305us
hdd0 80gb>> winxp, recovery partition, 1gb boot???(all factory>
hdd1 80gb>> ubuntu 7.10
512mb ram
128 vid mem


what id like to do is have grub ask me to load either xp or ubuntu
i edited menu.lst, i shows me an option to load xp, then it says staring...
.........
how can i do this dual boot?
thanks, steven

---

