---
title: "Installation will not recognize my hard drive"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by zzzPOOHzzz on 2010-03-03
I have 4 hard drives in my computer...
2x 74gb raptors
and 2x 640gb caviar blacks

i just wiped windows 7 from the first raptor to install linux... now when i try to install linux it tries combining the 2 raptors as a raid (which i don't have them set up for)
i just want to install it on my 1st raptor.

i disabled the dmraid and that took care of it trying to combine them as a raid, but then it won't recognize either of the raptors.

so i try gparted to format them. and i succeed.

but when i try to install again. it still doesn't recognize the raptors... and only my 640gb blacks
so i disconnected the power from the blacks... but to no avail, now no hard drives show up when i'm trying to install ubuntu... i am stumped.

sorry if that doesn't make much sense... ask questions and i will be glad to answer them, its very frustrating.

---

### Post by darkod on 2010-03-03
Sometimes removing dmraid is not enough. It seems to stubbornly think they are in raid so they might have raid meta data on them.

Boot into the live desktop, run:

sudo fdisk -l

to see the raptors names. Then, using the names of the drives, run:

sudo dmraid -E -r [COLOR=Red]/dev/sda[/COLOR]
sudo dmraid -E -r[COLOR=Red] /dev/sdb[/COLOR]

If it asks you to remove raid data, you're on the right path and after that you should have no problems seeing them in the installer.

---

### Post by simsypoo on 2010-03-03
I have a similar problem, I have 2 hard drives, a 160 GB WD and a 750 GB hard drive that I have for storing my media on (Pics / Vids / Music). 

The 9.10 install disk will not give me the 160 GB disk as a HD option, instead always bringing up the 750 GB drive. I can open up GParted and see both drives just fine however.

I'm going to work around the issue tonight by simply unplugging the 750 GB drive so there's only one drive for it to install.

---

### Post by darkod on 2010-03-03
> **simsypoo said:**
> I have a similar problem, I have 2 hard drives, a 160 GB WD and a 750 GB hard drive that I have for storing my media on (Pics / Vids / Music). 

The 9.10 install disk will not give me the 160 GB disk as a HD option, instead always bringing up the 750 GB drive. I can open up GParted and see both drives just fine however.

I'm going to work around the issue tonight by simply unplugging the 750 GB drive so there's only one drive for it to install.

Have you tried temporarily selecting the Erase and use whole disk option which enables the drop down list under it? If the disk is there you can select it, and then use another option not the Erase... one if you don't want to wipe the hdd.
It seems ubuntu tries to "guess" on which disk you want to install but doesn't always get it right. Maybe it goes by boot order and people rarely change boot order before installing on another disk.

---

### Post by zzzPOOHzzz on 2010-03-03
awesome thanks! bu now it hangs when i have to partition the drive... ugh... i'm gonna try doing it outside of the live session... tell you how that goes in a minute

---

### Post by zzzPOOHzzz on 2010-03-03
awesome... it worked... i am on my way... thanks again!

---

### Post by fraber01 on 2010-11-11
> **darkod said:**
> Sometimes removing dmraid is not enough. It seems to stubbornly think they are in raid so they might have raid meta data on them.

Boot into the live desktop, run:

sudo fdisk -l

to see the raptors names. Then, using the names of the drives, run:

sudo dmraid -E -r [COLOR=Red]/dev/sda[/COLOR]
sudo dmraid -E -r[COLOR=Red] /dev/sdb[/COLOR]

If it asks you to remove raid data, you're on the right path and after that you should have no problems seeing them in the installer.


YOU ROCK!!!

[COLOR=Red][COLOR=Black][FONT=Verdana]I had the same kind of problem, no disk displayed in the list.  After seeing your answer, I remembered it was a disk removed from a raid... tryed your command and voila! it worked! thanks!
[/FONT][/COLOR][/COLOR]

---

### Post by vollager on 2012-02-06
> **darkod said:**
> Sometimes removing dmraid is not enough. It seems to stubbornly think they are in raid so they might have raid meta data on them.

Boot into the live desktop, run:

sudo fdisk -l

to see the raptors names. Then, using the names of the drives, run:

sudo dmraid -E -r [COLOR=Red]/dev/sda[/COLOR]
sudo dmraid -E -r[COLOR=Red] /dev/sdb[/COLOR]

If it asks you to remove raid data, you're on the right path and after that you should have no problems seeing them in the installer.


 Man seriously you'r the MAN!!! that solved my problem, thanks!!!</br>

---

