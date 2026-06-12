---
title: "Installation Advice..."
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by gohmifune on 2008-11-15
Ok, so I'm buying a new HDD soon(anyone got any suggestions on brand reliability, let me hear 'em), in all likely hood a 320 gb 7200 rpm for my laptop, brand undecided. I will be dualbooting. Does anyone know anything that I should take precautions with. It's been a while, is it still windows first?

Also, is the alt. cd like the Debian installer? I know my Home partition will be seperate, but is there reason to have all the other folders(/var,/bin,etc..) seperate too? Any reason to not use ext3?

Any help is appreciated.

---

### Post by inobe on 2008-11-15
seagates are reliable.

xp first, just my opinion :)

be sure to create a partition for xp and let ubuntu take the rest, a 40 or 50 gigs wouldn't be bad if you mainly surf and email.

during the ubuntu setup' choose the free space, i believe one option would be use entire disk, meaning it will use and automatically create needed partitions on the 50 gigs of allocated space.

do not modify ubuntu's automated setup.

it is important to put xp on its own partition, the ubuntu install would be a walk in the park.

---

### Post by crazyness003 on 2008-11-15
Start online at [www.tigerdirect.com]("http://www.tigerdirect.com") and [www.newegg.com]("http://www.newegg.com"). You may be able to get some very good deals on HDD. Reliable too.

Seagate is good, but i've had more luck with Western Digital (WD). Try to stay away from OEM Maxtor drives, as they tend to be unreliable. The retail Maxtor ones should be okay (since Seagate bought Maxtor recently). Oh and definitely go with SATA (no question. its SATA or nothing). And forget RAID. Its overrated. 

EDIT: Whenever you get a WD drive that says 160gb, its really only 149gb. so be careful. You never get what you pay for. I dont know how the others compare.

Also, laptop HDD are the 2.5inch ones. Desktop drives are 3.5inch (FYI)

As for install. Yes, win first. Depending how bid the drive is, you may wanna give win more, since its a hog. Ubuntu runs on very limited space, very nicely, so i wouldn tworry about it not having enough diskspace. 20 gigs for Ubuntu is PLENTY (depending on where you store other personal data).

Partitioning. Do sda1:win(ntfs); sda2:docs(ntfs); sda3:root (all Ubuntu). 
Remember, win cannot write ext3 partitions (well anythign othr than FAT or NTFS) but can read with limited success; yet Linux can read/write just about anything (ext3, hpfs, ntfs, fat, xfs, reiserFS, etc). So by storing your data on the docs partition, you can access it from both OS's.
You can split /home if you wish, just so that when you upgrade a distro, it saves your app data, and preferences.

The alt CD comes with no liveCD run, and the installer is a psudo-gui. It gives you more options to choose frome, and has some advanced features, but if you had limited OS installs, id go with the regular.

When you do set up your parttition tables (in win install) make sure you leave free space after the last ntfs partition, so when Ubuntu installs, you just pick 'Install on free space' and you'll be sailing. (I personally like to manually edit all partition options, but i've done this mor than...well 100 times)

As for Ubuntu FS, id stick with ext3, since its jouitrnaled and I dont know anything about the rest. Plus gparted (the default Ubuntu partition editor) has excelent capabilities with ext3 (journaled).
If you decide to split your /home, you can set that as FAT32 if you wanna access it from windows aswell, but i've had limited success with that.

Well, good luck, and i hope you also do some self learning in the process.

(PS: it takes windowsXP about 1 hr to install, yet ubuntu can install in a matter of 20 minutes. from my personal experience)

Happy installing.

oh and another suggestion: DITCH WINDOWS. GO 100% UBUNTU!!! RAWR.  im kidding;)

---

### Post by Cool G5 on 2008-11-15
Get one from Western Digital. They are good. I too recently purchased a 640 GB SATA HDD 16 MB Buffer(Not for laptop).

For Installation:

#Install XP first

#Install Ubuntu

Just Install Ubuntu on a seperate partition, make a small(512MB) partition for swap & you are good to go with a dual boot system.

Don't touch windows partition and you are safe.

Good luck !!!

---

### Post by inobe on 2008-11-15
> **gohmifune said:**
> Does anyone know anything that I should take precautions with.


i would include the make and model of your laptop, maybe someone here can point out hardware issues for that model !

---

### Post by gohmifune on 2008-11-15
I'm less concerned with the issues with the laptop, I'm on 8.10 now(its Sager 2090, btw), but any drive issues. I'd assume some OS are friendlier under certain conditions, but its a small thing.

Thanks, everyone, the win first thing was the most important.

---

### Post by crazyness003 on 2008-11-15
> **gohmifune said:**
> I'm less concerned with the issues with the laptop, I'm on 8.10 now(its Sager 2090, btw), but any drive issues. I'd assume some OS are friendlier under certain conditions, but its a small thing.

Thanks, everyone, the win first thing was the most important.

word. and good luck

---

