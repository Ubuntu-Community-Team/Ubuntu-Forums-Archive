---
title: "Ubuntu installer hangs at partition"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by xyZen on 2007-06-15
Using the ubuntu 7.04 dvd i got off some linux magazine or other, i have managed to achieve the following steps when attempting to install:

put the cd in, got the desktop to load.
Click the install icon
selected my language and keyboard
the next step (4 of 7), the installer scans my hard discs, then nothing happens.


ideas? suggestions?

the only thing i can think of doing at this point is to re format one of my hard drives, disconnect the one with XP on it and try and re-run the install on the new "clean" drive, but im not sure if that will make a difference.

my system is as follows:

p4 3.2ghz
1.5 gb ram
1x 120gb hdd (set as master with XP on)
1x 320gb hdd (set as slave)

any help would be greatly appreciated :)

---

### Post by musther on 2007-06-15
It could be a filesystem issue, try using XP or a live CD to check the partitions.  Also, the installer checks for windows users to import stuff, how long did you leave it before deciding that it didn't work?

Or you could try downloading an official CD, sometimes these mags mess with them and then you have issues.  Or, failing that, download the alternate installer CD.

Sorry I can't be of more help.

---

### Post by xyZen on 2007-06-15
i left it for 10 minutes before cancelling the installation.

In theory i dont have any partitions- both hard drives have been formatted to use XP- if i reformat one of them in DOS, will it automatically set it up as NTFS?

---

### Post by musther on 2007-06-15
No, if you format in dos it will probably be FAT32, that's if you mean a DOS bootdisk.  

If ther's nothing on your partitions, what are you planning to do, are you trying to install Ubuntu and then Windows?  If that's the case, you'll most likely find it easier to install windows first.  

If there's no reason to keep the current partitions, then boot the live CD, go to system --> administration and use the partition editor to repartition you disks, format them to what you want, and then install.

---

### Post by bmartin on 2007-12-12
I can confirm this problem. On both the Gutsy and Feisty CDs, the installer hangs on my computer right before the partition step (after you select your language, which for me).

I used GParted to set up the partitions to my liking, mounted/unmounted them to test them out (not that it should really matter), and it still doesn't work.

This is a pretty serious bug. I looked on Google, but alas, I found no helpful information at all. I'm going to try with the alternate CD, provided I can download it before lunch, which is when I'm going to try installing again. If the CD isn't downloaded by then... well, PCLinuxOS only took 30 minutes to download. As long as I can get Fluxbox running on there, I'll be happy.

---

### Post by bmartin on 2007-12-14
There's an NTFS program on the Live CD called ntfsresize or something like that. If you go to the step where the partitioning starts, then open up a terminal and run **top**, you can see that it's using 100% of the processor (indefinitely?).

The way around this for me was to rename the program. It's located in /sbin, I believe. You can use the **which** program to find out. Anyways, I renamed it to ntfsresize.old or something like that, then ran the installer and everything worked fine. This was acceptable, because I was partitioning a drive and destroying all old partitions. This would be unacceptable for someone that wanted to resize their partition.

Anyways, I hope someone benefits from this information.

---

### Post by #sKiLLy on 2008-01-17
Sadly I ran into this today too :(

---

### Post by bmartin on 2008-01-17
Did my recommendation help you out at all? If you need to, contact me on AIM or Google Talk and I can walk you through the steps to get around this issue.

---

### Post by Xtov on 2008-02-17
I had this when trying to install on a 400GB NTFS drive.  In this case, size may matter.

To get around this, before installation (when running for the install CD) go to;

System -> Administration -> Partition Editor...

And manually reformat as a non NTFS partition (I did ext3), then do the install as normal.

This seemed to work (for me)


Regards,


Xtov

---

