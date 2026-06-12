---
title: "trying to install ubuntu, not working, freaking out!"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by oilspot on 2008-10-23
I've been using windows xp for years. I restore everything once a year to try to keep it running well.
 A good friend told me to try ubuntu. I tried the "run from disk" version and loved it.

 I decided to use the partition setup deal that comes with the ubuntu setup disk (that I burned). 
 I've got a 300Gb hardrive so i figured I'd use 150 for windows and 150 for ubuntu. 
 During, the computer locked up and did not respond, to the point where I had to pull the plug. Now I can't get the computer to boot windows. I can only get it to boot ubuntu using the disk.
 
 I've got some stuff in windows that I would really like to get, but if I loose it the world will not end.
 I tried to run the setup for ubuntu and it fails and says there's a problem with my disk. I ran the disk test and it says it found one problem.


 What do I do?

As you can tell from my rambling I'm not the most knoledgeble about computers. I can usually make stuff work but this, has me stumped.

---

### Post by lswest on 2008-10-23
How long did you give the computer to respond?  Resizing a 300GB partition to 150GB can take a while, especially if it's NTFS.  chances are you interrupted it while it was moving and resizing the partitions, making windows unbootable.  You should be able to access the files, however.

If you go to the "Places" menu, it should show your windows drive, clicking it should open it so you can move/back up the files you want (to a flash drive or external hdd), and then decide how to continue (just in case).

Post back if this isn't the case.

---

### Post by oilspot on 2008-10-23
I let the computer sit overnight thinking it may just be taking a while to partition. It was in the same place that I had left it the night before.
 I looked in the places tab. It doesn't show anything as far as a second (windows) partition. 
 Windows will not boot. Fearing the worst. My wife said she's got a few work documents that she needs before I can just kill windows. As soon as I can hopefully retrive those documents I'm ready to just run ubuntu as the only operating system on this computer.

 I'm thinking there may not be any way to retrive what I lost in windows. If thats the case is there an easy way to wipe the hardrive, and just start fresh installing ubuntu?

---

### Post by zvacet on 2008-10-24
Look under **places>filesystem** and maybe you will see Windows folder.From there get a fils you want to keep.All night is long time so maybe you should try** alternate CD**.You can allways delete Windows when you get to the partition stage.

---

### Post by bro on 2008-10-24
you are probably right to worry. But have you tried it with a windows boot cd? You R (repair) and fixmbr (or what is the command? fix mbr?). If it doesn't boot at all, windows might just have to fix the master boot record before it finds itself. 

To be honest, this might very well work - but because of the partitioning phase in which it crashed... :???:

---

### Post by oilspot on 2008-10-24
Theres no windows folder. Under places it's showing no signs of a partition. 
 My wife is pissed that I "messed up the computer". She doesn't care if we use ubuntu because she's seen over time how unstable windows can be. Not being able to get the files that she wanted out of windows isn't that big a deal.

 So...

 Is there a fairly simple way to  wipe the hardrive completly so that I can do a full install of ubuntu? I'm glad that I can run this off the disk but it defanantly has it's limitations!
 I don't have a windows disk, and will have to make the calls to try to get a copy. 

 If I can get this fixed before my wife comes home this afternoon that would be great!!! It'll make my weekend go way smoother!

---

### Post by mariuskl on 2008-10-24
You can see the partition in which you have windows? Have you tried to install windows instead ubuntu in the ubuntu partition ? Just to not loose your informations.

---

### Post by oilspot on 2008-10-24
remembered after posting seeing an option to install using the entire hardrive for the install of ubuntu. So I gave it a shot. 
 Install ran right up to about 73% and then quit.
I got a message that said I could have a bad or dirty cd, dirty lens, or possbily a faulty hardrive.

 I can't use this computer to burn another disk, I've got to leave the disk in the drive for anything to keep running. I'm thinking about hooking up my wifes laptop and burninig another copy of the install disk.
 
 I don't have much faith that it will work, but I figure I should start at the easiest answer and then work my way up.

---

### Post by oilspot on 2008-10-24
Burnt another iso disk. Did the full installation. Worked flawlessly.
Very humbling! 
 Still no windows! Have a friend that I'm going to have come see if he can find any traces of what used to be.
 
 Mabey I should have backed everything up before I started the install:). You would think somebody may have said that in the install instructions... oh yeah... they did.... quite a few times!

 I'm just happy to have a fully functioning computer again. I'm sure I'll be back with loads of questions!

---

