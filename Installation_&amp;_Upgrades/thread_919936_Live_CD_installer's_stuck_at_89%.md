---
title: "Live CD installer's stuck at 89%"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by KATHYxx on 2008-09-14
Right now I am trying to install Hardy on a HP pavilion laptop from scratch. Originally I was just trying to update from Gusty, but it hung on the locales and the conventional solution didn't work. So i ended up trying to reinstall with the live CD from scratch (everything is backed up so I don't care if I have to reformat). 

Installation worked seemingly ok until the Installing System window appears. It stopped at 89%.. "Checking for packages to remove." The first time this happened I quit the installation only to find out that GRUB has been hosed and my computer will not boot at all,not even to Windows XP, without the live CD. On the second attempt it is stuck again and I've just left it sitting there. 

dpkg, klogd and dd seem to take up the entire CPU doing nothing, at 29% usage apiece.

I tried fixing GRUB, but it seems to have completely dissappeared.. i tried backing up /boot/grub/menu.lst but that doesn't exist. /boot doesn't seem to have any subfolders at all. At startup it just says Error 22.

If possible, I'd like to get GRUB back up to see if my Windows XP partition somehow survived all of this.. and in the best case   I'd just want to have both systems dual booting again.. Thanks in advance, and i apologize if this is a double post though i can't find this issue using search.

---

### Post by shellback84 on 2008-09-14
I am guessing that like me, you are new to Ubuntu. If that is the case, we do not have the tweaking skills that the expert Linux users possess. My point? 8.04 has been a pain the the rear and you would not believe the hoops I have gone though to finely get it to work in my computer. I have spent weeks to months finding tweaks and waiting for updates. 7.10 was much easier and gave you more options for many hardware tweaks that for some reason they opted to toke out of 8.04. I know there has been a grass root effort to make Linux easier but taking out important tweaks is not the right way. I am sorry as I am complaining and I will not be much help to you but some of the people on here are very good with the terminal commands and my guess is that using the terminal will be your only way as that was the only way for me, thanks to the help here. Good luck and it can be done.

---

### Post by KATHYxx on 2008-09-15
Oops,  I meant grub has an Error 22 at startup, not 24. I edited the post.
something to do with partitions.. 

I forgot to mention that I tried to configure the partitions manually, since "use contiguous free space" made the partitioner want to attack my windows part anyway for some reason. I'm not sure if I did it right, now that i think about it.
I made 15 GB into the biggest part, a 630 MB swap, and a 230 boot.. that is what Gusty appeared to be using, judging by the partitioner. 

I've been an Ubuntu user since February. i got it mostly for programming but I've been pretty much satisfied with it until now. The only things are this debacle, and that my puny laptop graphics can't handle all the windows programs under Wine, which is why I hang onto windows. I can't tell you how long I've been trying to upgrade this before i tried coming here...

---

### Post by KATHYxx on 2008-09-15
fdisk info.. in case this is useful since i am worried about the partitions

```


device     boot     Start     End         Blocks     ID    System
/dev/sda1   *             63  165598019  82798978+    7    HPFS/NTFS
/dev/sda2          194948775  195366464  208845      83    Linux  
/dev/sda4          165598020  194948774  14675377+    5    Extended
/dev/sda5          193615443  194948774  666666      82    Linux swap / Solaris
/dev/sda6          165598146  193615379  14008617    83    Linux



/dev/mmcblk0p1            57      31359  15651+       1    FAT12

```








Edit: Here's a rather weak fix: 
I got an old alternate gusty installer, used it.. though it failed to install too, the next time i tried a different Hardy live CD i got from a friend and it installed perfectly. Figures... when i try to fix something with reason and logic it makes it worse, but doing something that seems to have no impact fixes everything.

---

