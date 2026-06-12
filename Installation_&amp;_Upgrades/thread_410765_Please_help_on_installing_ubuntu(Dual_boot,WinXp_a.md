---
title: "Please help on installing ubuntu(Dual boot,WinXp and Ubuntu)"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by udd2006 on 2007-04-16
Hello all,
Iam newbie here and to ubuntu server  6.10 .I want to install ubuntu on my laptop hp dv5000 with ram 512mb  hadr disk 60gb.I have donwloadined and burned the iso image.The problem Iam facing is I dont want to loose Win Xp, done backup ready.Is there any option on ubuntu which can help me to partition my hard disk in( C and D)  without  deleting the WinXp?.which option  among three option in ubuntu wizard partition?.if not can anyone point me for free partion tool?.I have tried the following tools,partion logic,ranish but all didnt work,gave me errors.
I will really appreciate for your help.
Thanks
Udd2006

---

### Post by nsleiman on 2007-04-16
why dont you try to partition your hardisk using partitionMagic or something for windows? you can do this with linux tools also but there is always a risk that your windows os can break (surprised?)

after doing this make one small partition for swap use (800mb enough i guess)

---

### Post by Spr0k3t on 2007-04-16
If you are using Edgy (6.10) you can load the LiveCD and shrink the size of your main partition.  The application will be under the System::Administration menu.  I've heard it works better than PartitionMagic (never used it).  Just to be safe, make sure the system is backed up as always.

---

### Post by zvacet on 2007-04-16
Defragment win partition few times before you shrink it.You can use [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") to do that.When it is all done install Ubuntu on free space.

---

