---
title: "Multiboot Linux and Windows on the same harddisk??"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by 0vermind on 2005-11-30
-NOT EXACTLY SURE IF THIS IS THE CORRECT PLACE TO POST THIS-

Hello,

I have a 120 GB Hard-Drive and don't use the entire thing..... is there a way that i can automaticly partition a partition, casue I'm resizing the and making 10 GB avaible for multiboot for linux before with a single harddrive i was able to select the opiot "Automaticly Partition Hard-Drive" and it would split the space into three partitons..... Sawp, EXT, and the OS.

How do I do this with multiboot??? 

In case you need to knmow I'm using:
120GB Western Digital Hard-Drive with Microsoft Windows XP Professional SP2

Thanks in advace for any help or ideas,
MIKE

---

### Post by rykel on 2005-11-30
[QUOTE=0vermind]-NOT EXACTLY SURE IF THIS IS THE CORRECT PLACE TO POST THIS-

Hello,

I have a 120 GB Hard-Drive and don't use the entire thing..... is there a way that i can automaticly partition a partition, casue I'm resizing the and making 10 GB avaible for multiboot for linux before with a single harddrive i was able to select the opiot "Automaticly Partition Hard-Drive" and it would split the space into three partitons..... Sawp, EXT, and the OS.

How do I do this with multiboot??? 

In case you need to knmow I'm using:
120GB Western Digital Hard-Drive with Microsoft Windows XP Professional SP2

Thanks in advace for any help or ideas,
MIKE[/QUOTE]

hi mike,

with 120GB available, i would suggest the following partitioning scheme:

[INDENT]10GB - Windows XP
10GB - Ubuntu root (/) - use ReiserFS
10GB - /home - use ReiserFS
1GB - Swap
MAX - /windows/d - use FAT32[/INDENT]

hope tat helps!!!

---

### Post by nab on 2005-11-30
Hi,

 Short answer: 
no, you can't automatically shrink your windows partition and setup ubuntu inone step.

I did it the following way: 

1) Backup your whole disk and make sure the backup is working ;) 

2) Clean-up your windows system (e.g. defragment your disk)

3) Resize your windows partions with your favorite programm 
   (some live-cd's have partitions editor - e.g. qparted or gparted - on bord)

3) Test windows is still working.

4) Start ubuntu-installation

5) choose manual partitioning

6) You will see in the partition table your windows partitions as ntfs or fat32
   (depending how your system is setup)

7) In the free space you divide your disk and name the partitions as rykel suggested.

8) Rest of installation should work fine.

Hope this helps and answers your question

Niko

---

### Post by 0vermind on 2005-11-30
the problem is I don't have a resizing tool either and i want to have the following setup.....

-HARD-DRIVE 120GB-

Ubuntu Root - 9 GB
SWAP - 2 GB
Ubuntu Home - 7 GB
Windows XP - 10 GB
Windows Storage - 61 GB
Windows Extra Partition - 20 GB
Network Partition - 1 GB
Windows Backup Partition - 8


Is it possible to have 8 Partitions????

And about the Partitioning tool I would perfer if it was non-dos and it MUST BE FREEWARE!!


Thanks :smile: ,
MIKE

---

### Post by bwog on 2005-11-30
The resizing tool is in the install CD, it is part of the install procedure if you need it. It is self-explanatory, but if you need help dont continue but ask a question here. Dont use a windows tool.

I think it is practical to make the windows install partition larger if you have the space for it. It tends to fill easy, but it also depends on what you use it for.

You can make 4 primary partitions and as many logical partitions as you want to.

One more thing: if you use 18 GB for ubuntu make a root and a swap partition (1GB swap is probably  enough).
When you have more space make 5  GB / (root), 1 GB swap and the rest  /home. Home is where all your data will be, so you need the most space there.. It is better to have a separate home directory in case things go wrong. 

Good luck

---

### Post by aysiu on 2005-11-30
Back up your work.
Then follow this tutorial:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Talisker on 2005-12-01
May I hijack the thread? ;) 

I run a AMD64 bit Laptop with a 40 Gig HD. I did run the Live CD previously on 32bit (32bit Live CD) and it did find everything but the Ralink Wifi.

Anyhow, now I'd like to install the 64 version on the Laptop, to get used to and play with it. Later I probly get a bigger HD and make a decent setup. 
Question:

For multiboot, what would be a useful partinioning to get started with Ubuntu?
(HD is formated NTFS)

Whats a good backup software to make a ghostcopy of my current HD?

Thanks;)

---

### Post by bwog on 2005-12-01
Just to try the installed version, you can make 10 GB free and let the installer partition it.  

However, check first how much space you have left and defragment the windows disk. The idea is to leave lots of space for windows so that you can continue to use it. 
When you are new to linux try the i386 version first,  the 64bit OS is harder to operate at this moment.

good luck

---

### Post by Talisker on 2005-12-02
In what way is it harder? Power management issues?

I'm downloading the 64bit Live iso now... guess we'll see what happen...*S*
The 32bit worked fine. It just doesn't make sense to me running a 32 bit programm if the 64bit is available.
The weekend is not far... lots of time to play with Ubuntu ...*S*

---

### Post by Talisker on 2005-12-02
[QUOTE=Talisker]In what way is it harder? Power management issues?

I'm downloading the 64bit Live iso now... guess we'll see what happen...*S*
The 32bit worked fine. It just doesn't make sense to me running a 32 bit programm if the 64bit is available.
The weekend is not far... lots of time to play with Ubuntu ...*S*[/QUOTE]
Nevermind.... after browsing the 64bit help section..... I'll install the 32bit version...*lol*

Seems Ubuntu is not quite 64bit ready...*S*

Thanks for the advise

---

### Post by akiro.yamamoto on 2005-12-02
Linux has had 64bit support for a while now..the trick is that to get the full benefit your software should also have 64bit capability..not only the underlying OS but your favourite prog as well.
You might want to check the 64bit Forum section. To have a better idea of the type of problems and solutions the typical user might experience after making the switch.
Regards

---

