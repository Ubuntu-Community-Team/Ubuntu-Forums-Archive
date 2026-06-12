---
title: "Repartitioning Drive"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by sq2shooter on 2007-06-02
I am officially over my head and do not know what direction to go in. I installed Edgy Eft to dual boot on a XP Vaio laptop. The entire experience went flawless. Fast forward to Feisty fawn's release and I was unable to upgrade no matter how many attempts I made. The upgrade manager would either time out or give multiple errors. I eventually just downloaded the ISO and installed it after burning it to CD. Being slighlty nervous about it, I left my original Edgy install partition. So now I have a functional Feisty install. It is working great. Problem is that I now have my hard drive partitioned into three OS's and I no longer need the Edgy install. I am left with my 7.04 partitioned on only 10 gigs while my Edgy install is wasting 20 gigs (the remaining 30 gigs is for my XP). I would love to eliminate the Edgy install and give that space to the 7.04, basically just splitting my drive 50/50 with the XP. Is it possible to do this without having to uninstall both Ubuntu builds and reinstalling the 7.04? If this is possible, could someone point me in the right direction to accomplish this? Thanks for the help.

---

### Post by Herman on 2007-06-02
Hello sq2shooter,
You upgrade the same way as I always do. It's a better way to do it anyway. 

You can do everything you want with your partitions and filesystems if you get [GParted -- LiveCD]("http://gparted.sourceforge.net/"). That has the latest version of GParted which has been able to move Linux filesystems and resize them from the start point (left) for quite some time now, (over a year I think). 
I would just resize the old Ubuntu as small as I could and just keep it for a standby system for a while. It will probably only occupy about 2 to 5 GB of disk space if all the data is gone, (depending on how much software you have in it).
If you do delete it that's okay, just check your /etc/fstab file first and see if it has an entry for that partition in there. If it does you should comment that out or delete that first. If you forget it will stop at a black screen for the filesystem check during boot-up and you'll have to press 'ctrl+d' for it to continue booting. Be careful which line you delete or comment out, that's all.
I have a nice big hard disk and much data, so I just have my hard drive split Windows 10 GB (I never use it anymore), and Ubuntu 34 and 35 GB, plus a 1 GB swap.
Right now my old Edgy install is still there but all my data is in Feisty. When Gutsy gets okay enough for me I'll install that in my old Edgy partition and when it's released I'll move the files into it and vacate the old Feisty operating system,.
I never bother trying to upgrade my system to the next verson, I like having everything new again each time. It only takes a few minutes to transfer my files.
Well that's all for now, I hope it helps,
Regards, Herman :D

---

### Post by Wim Sturkenboom on 2007-06-02
You can use the 20 GB as a home partition for Feisty.

---

