---
title: "Can't install Ubuntu!?!"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by archangelmorph on 2007-02-04
I have serious installation problems,

I'm seasoned Windows user who decided to try out Ubunto for the first time. I'm a complete noob when it comes to linux OSes and so ordered the install CD from Shipit..

Anyway my CDs arrived and I setup my machine ready to start the installation process..:

My PC:
AMD Athalon 3500+ 64-bit CPU
Asus A8N-SLI duluxe mobo
2 Gigs RAM
Geforce 7800GTX gfx card
1x 40GB maxtor HDD
1x200 GB SATA maxtor HDD

WinXP (no SP, installed on the SATA HDD..)

Ubuntu (Dapper Drake)


So anyways I disconnected my SATA HDD which contains my XP install and all my personal data and loaded up tha machine with the 64-bit Ubuntu CD in the drive..

**ERROR 1**
I got to the "Start or install Ubuntu" screen and selected that option..
It began loading and got as far as mounting the root file system and hung.. I tried multiple times with that CD and the same thing happened every time..:confused: 

I then mounted the 32 bit version of Ubuntu and managed to load into the live OS..

**ERROR 2**
From there I started the install procedure and got as far as the partitioning setup of which I selected the "erase all and install Ubuntu" option.. I then proceeded to begin the installation phase when it throws up an error telling me that there was an error creating the swap space.. on clicking ok the installation proceeds upto 15% (detecting file systems...) and then stops responding.. The disc slows down at this point and stops spinning.. closing down the installation window takes me back onto the desktop but when i double-click the installation again nothing happens..:confused: 

So then I try the installation again but this time, after doing the following:

 - reconnecting the SATA HDD
 - loading win XP and deleting all partitions on the 40GB HDD
 - disconnecting the SATA HDD and loading into 32 bit Ubuntu again

once i get to the partitioning bit again i decide to take the other route and manually create a partition for the ubuntu install. Upon loading into GPart it displays the HDD as the full 37.49GB unallocated space (strangely enough it showed this before when I first attempted an install and before i'd deleted all win XP NTFS partitions off the drive.. these partitions were visible in windosXP when i deleted them but not in Ubuntu's GPart for some reason.. ???)...

**ERROR 3**
when I attempt to create a volume label i click on advanced and then select an msdos volume label.. when I click on create i get an eror msg telling me that there was an error creating volume label and then doesn't do anything else.. after going back and attemptig to erase the disk again and install it repeats the same error in ERROR 2...

I really don't know whether there's a fundamental problem with my hardware configuratuion and Dapper drake or if there's something I need to do but am not doing to get this OS to install.. :confused:

I desperately need help on this one.. :(

---

### Post by archangelmorph on 2007-02-04
Pls help! :(

---

### Post by pauljwells on 2007-02-04
you might have more luck with the alternate install CD - it has a text based installer.

---

### Post by citizenofnowhere on 2007-02-04
I've found that Gparted on Dapper was a little less than friendly to SATA disks (like the one I have on my laptop). It showed errors that weren't really there.

Luckily, there's another way to partition your harddrive pretty painlessly - the Gparted livecd. It's like 25mb worth of a download so its feasible even on a very slow connection, and it's an invaluable tool for anything, even ntfs partitions.  You will find it [here]("http://gparted.sourceforge.net/livecd.php").

I'm not entirely sure if it's hardware OR Ubuntu, it could be a kernel thing. I know the problem is no longer there in Edgy. After you partition using the livecd, you should be able to manually tell the installer where the mount points go (your root partition or /, your swap, your /home if you want it to be separate (not always a bad idea)). Tell it to not format anything since you've already done that, and you should be ok.

Hope this helps!!

---

### Post by archangelmorph on 2007-02-05
Thanx for the help!

I'll give it a try and see if it helps!

The other issue is the problem with the 64 bit version, do you think there could be a problem with the disk or?

---

### Post by citizenofnowhere on 2007-02-05
Well I really can't say for certain, I've only ever tried to install a 64 bit edgy once, which is by no means a statistic but that didn't go very well - the installation hung round about halfway and looked a little scary. Assumed it was a bad download.

Dapper 32 bit worked beautifully though on the machine (it was a amd64 fujitsu laptop).

---

