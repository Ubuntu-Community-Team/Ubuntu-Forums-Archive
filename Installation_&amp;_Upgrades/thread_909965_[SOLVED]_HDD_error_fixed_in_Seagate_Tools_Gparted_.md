---
title: "[SOLVED] HDD error fixed in Seagate Tools Gparted still complaining"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by Lateforgym on 2008-09-04
Gparted says there is an error on my primary, but Windows and Seagate Tools says its ok. There was one bad sector that Windows didnt catch, but Seagates deep search found and repaired. After two more runs Seagate says the drive is without errors. Should I trust Seagate or gparted? :-)

I dont trust that gparted catch a "bad sector" in the amount of time it takes to load gparted, that Seagate's Tools cant in over an hour of checking sector by sector. Gparted has to be throwing a false "bad sector" error. 

Im wonder if there is some system file that is marked as "cant be moved", kind of like when you defrag and it tells you certain things just arent going to be moved.  

I may have to pass on the install if it cant shrink my primary. I have waaay too much time into tweaking XP to want to wipe the HDD, load Windows and Ubuntu and tweak everything to where I want it.

---

### Post by caljohnsmith on 2008-09-04
> **Lateforgym said:**
> Gparted says there is an error on my primary, but Windows and Seagate Tools says its ok. There was one bad sector that Windows didnt catch, but Seagates deep search found and repaired. After two more runs Seagate says the drive is without errors. Should I trust Seagate or gparted? :-)

I dont trust that gparted catch a "bad sector" in the amount of time it takes to load gparted, that Seagate's Tools cant in over an hour of checking sector by sector. Gparted has to be throwing a false "bad sector" error. 

Im wonder if there is some system file that is marked as "cant be moved", kind of like when you defrag and it tells you certain things just arent going to be moved.  

I may have to pass on the install if it cant shrink my primary. I have waaay too much time into tweaking XP to want to wipe the HDD, load Windows and Ubuntu and tweak everything to where I want it.
Gparted, to my knowledge, can not scan for bad sectors. When gparted says your primary has an error, it could mean your partition table is messed up. Try doing the following from a Live CD:
```
sudo apt-get install testdisk
sudo testdisk
```
Then "create log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors (if any) that it gives. Please post the output.

---

### Post by Lateforgym on 2008-09-05
It wouldnt work from Livecd so I yanked the HDD and used a USB adapter and checked it through my Linux Laptop. Says structure is "ok". But it takes 2 seconds for it to make that distinction, I would have thought is would so some deep scanning. 

Anyway, I still dont get it. Every utility program(Seagate,testdisk,Windows error checking) except gparted says my disk is ok. 

BTW it doesnt print a log file in the VAR/log folder

---

### Post by caljohnsmith on 2008-09-05
> **Lateforgym said:**
> It wouldnt work from Livecd so I yanked the HDD and used a USB adapter and checked it through my Linux Laptop. Says structure is "ok". But it takes 2 seconds for it to make that distinction, I would have thought is would so some deep scanning. 

Anyway, I still dont get it. Every utility program(Seagate,testdisk,Windows error checking) except gparted says my disk is ok. 

BTW it doesnt print a log file in the VAR/log folder
You're right, I don't think testdisk is on the Live CD, so you would need an internet connection to download it while running off the Live CD. Also, testdisk creates its log file in the directory in which you run it from. 

Just so I can check it, would you post the output of testdisk after you select the "analyze" function? And just for completeness, have testdisk do a deep scan: from the beginning, "create log", select HDD and "proceed", "Intel", "Analyze" (post this output). Then do "proceed", "Y" only if you have a Vista partition, hit enter and select "search!" so it does a deeper search (which will take a while). Please post the output of its results when it's done. 

Also, is your primary HDD IDE I assume?

---

### Post by Lateforgym on 2008-09-07
Thanks for they reply, Im closing this as I tried to repartition with Partition Magic 8 and it complained too and screwed up my XP install at the same time. Unfortunately I have spent many hours on this with little success and need to move on. 

After much searching the net I did manage to find one other person with the same problem as me and the consensus was to trash the drive. Even though three check programs say its ok and SMART has not thrown a flag, two partition programs with different OS's say my drive have bad sectors. My drive is about 5 years old and has been through a lot, plus with my XP now running screwy, I might as well get a new drive since Im going to have to reinstall.

---

