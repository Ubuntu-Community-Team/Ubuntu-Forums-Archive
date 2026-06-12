---
title: "dual boot install"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by txm0523 on 2005-12-01
Greetings,

I currently have a Compaq Evo N1015v laptop with Windows XP home running a C: partition ( NTFS ). I also have a D: partition ( FAT32 ). I would like to install Ubuntu 5.10 ( have CD ) onto the D: partition and then have a dual boot option at startup, Windows and Linux. If I restart laptop with Ubuntu CD in drive, will I be able to install Ubuntu 5.10 without ruining my Windows OS ?  Will the installation process recognize that I have another OS and the D: partition ?

Also, if the above mentioned install is possible, I should be able to change from the default GNOME desktop to KDE. Is that still possible ?

Can anyone answer these two questions with certainty ?  I would appreciate any help.


Thanks

---

### Post by jasmuz on 2005-12-01
Yes, complete dual boot installation is possible. But you will have to point your installer CD to use the FAT32 partition (it will reformat that area and place an EXT3 partition).

after instalation you can open a terminal and type sudo apt-get install kde

Im sure that covers what you need.

---

### Post by aysiu on 2005-12-01
Just to reiterate...

the D: will no longer be D: any more after you format it as Ext3 and install Ubuntu there.

For more info on Ubuntu/Windows dual boots, see this link:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by MRCuadra on 2005-12-01
Okay, I am a complete Linux newbie, but I can answer some of your questions, because I just went through this last night...

> **txm0523]If I restart laptop with Ubuntu CD in drive, will I be able to install Ubuntu 5.10 without ruining my Windows OS ? Will the installation process recognize that I have another OS and the D: partition ?[/QUOTE]

Yes, and yes. :)  When the install gets to the "partitioner", it will tell you what existing partitions it found, and then ask where and how you want to handle installing Ubuntu. If you select "[FONT="Courier New"]<No>[/FONT]", it will give you a detailed view of the physical drives, and the partitions it found. "NTFS" should be listed on your "master" drive ([FONT="Comic Sans MS"]C:[/FONT]), and something like "FAT 32" should be listed on your "slave" drive ([FONT="Courier New"]D:[/FONT]).

From there on, it can get tricky, but that's mainly because I tried to setup my  drive like the experienced Linux users suggest:

one partition for [FONT="Courier New"]/[/FONT]  (a.k.a. "root", for the system files)
one partition for [FONT="Courier New"]/home[/FONT]  (for your user files)
and one for [FONT="Courier New"]swap[/FONT]  (memory usage)

Rather than getting specific about why, I suggest searching the forum(s) for things like 'partition' and 'suggest' (that's what I did).

Anyway, I'm still trying to get my install to work (there's appearantly a problem with using [FONT="Courier New"]FAT32[/FONT] for [FONT="Comic Sans MS"]/home[/FONT] said:**
> GRUB[/FONT] came up and I could select from various Ubuntu options, and at the bottom was "[FONT="Comic Sans MS"]Microsoft Windows 2000 Professional[/FONT]". I've been in and out of it a few times today, and I can't see any problems. (...with Windows, anyway :rolleyes: )

Now...

[QUOTE=txm0523]Also, if the above mentioned install is possible, I should be able to change from the default GNOME desktop to KDE. Is that still possible ?

This one I don't know. I don't remember there being a specific option for one or the other during the install, so somebody else can field this question.

Good luck!

MRCuadra
A Space In Time
----
"Any sufficiently advanced technology is indistinguishable from magic."  - Arthur C. Clark

---

### Post by bruce147 on 2005-12-01
Before you install, I recommend that you make sure you have a windows install disk or some access to the windows Recovery Console (and watch out for the password issue). You might have to use fixmbr or fixboot to get windows back. 

I have installed Ubuntu 5.1 three times using the standard install procedure. Each time it installed Grub in the windows MBR even though I had selected an install in the linux root partition. My original intention was to either use windows ntloader to control which OS to run, or to use an old copy of Partion Magic for OS booting. 

I am still not entirely happy with the placement of Grub in the MBR. On one occasion I accidentally caused grub to crash and my system would not boot any OS. I ended up reinstalling ubuntu so that it would reinstall grub in the MBR and give me access to Windows again. 

Here is how I crashed grub. Don't do what I did. After installing Ubuntu, I explored and tried to customize. Before a major customization, I used True Image to make a copy of the whole linux partion so I could restore it in case I really screwed things up. At one point an automatic kernel update occured. That worked fine, but it put several new enteries into my grub menu. Then came the day when I restored one of my older backups. I guess grub crashed because it was expecting a new kernel for its default choice, but could only see my old backup kernel. I guess that's what did it.

However, I don't want to discourage you from trying ubuntu. I am still using it and I am quite impressed. It may take some work to get all your laptop features up and running, but for me, that has been part of the fun (to a degree). 

So try it. Just make sure you can run fixmbr or have some program like true image that can backup your windows c partion and the MBR.

---

### Post by Ptero-4 on 2005-12-01
About the partitioning, yes ubuntu recognizes M$ Windoze and the separate partitions out of the box, it'll use your D: partition.

About KDE, you can dl the kubuntu CD and use it instead of the ubuntu one, or you can install ubuntu and then run apt-get install kubuntu-desktop. They get you kde either during install or afterwards.

---

