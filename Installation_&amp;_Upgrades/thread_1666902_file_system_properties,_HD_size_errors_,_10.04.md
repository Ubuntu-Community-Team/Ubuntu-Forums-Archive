---
title: "file system properties, HD size errors , 10.04"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by KAc on 2011-01-14
I have recently started with ubuntu 10.04 
when i installed it i made sure i hads plenty of space left on the HD (about 5GB), but when i try to install the necessary updates, i am told i only have a few hundred MB left.
to add to the confusion,file system properties : 193,774 itesm totalling 120.0TB (some contents unreadable), i have the screenshot handy.  believe me i do not have quite such a large HD, its more like 60GB, but i cant check this now can i!
i have run sudo aptitude clean ("sudo apt-get clean" didnt do much) which gave reports on variuos as "done" but no change to the errors, and the wastebasket is empty for the record.

---

### Post by Kirboosy on 2011-01-14
So you gave the whole Partition only 5 Gb?

This is problematic because Ubuntu fresh installs take about 5 Gb.


**Ubuntu Desktop Edition**

 
[LIST]
[*]1 GHz x86 processor 
[*]1GB of system memory (RAM) 
[*]**15GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily) **
[*]Graphics card and monitor capable of 1024 by 768 
[*]Either a CD/DVD Drive or a USB port (or both) 
[*][Internet access]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") is helpful 
[/LIST]


Are you trying to do a separate OS and home partition?

---

### Post by KAc on 2011-01-14
not quite, squire. actually, i have a n empty 40.8GB HD, and i didnt partition it myself.   it should all be good to use.   the vista-windows on another drive advises there is nearly 6GB free, despite this Ubuntu offer me about 300MB.  the vista says it has 35G used on this dirive after the install.
i dont know what you mean by separaet OS and home partition, its all home, but i have Cdrive with vista and D with Ubuntu.

---

### Post by KAc on 2011-01-14
correction its not an empty 41gb, it has ubuntu and other stuff, leaving 5gb for installs which ubuntu doesnt seem to aggree with...i am deleting some stuff, maybe thatll be a workaround but i still dont get the discrepancy...

---

### Post by KAc on 2011-01-14
correction its not an empty 41gb, it has ubuntu and other stuff, leaving 5gb for installs which ubuntu doesnt seem to aggree with...i am deleting some stuff, maybe thatll be a workaround but i still dont get the discrepancy...

---

### Post by KAc on 2011-01-14
oK, so i have some more info:

the drive now has an extra 5GB, totalling >10GB free and available.  I deleted files via VIsta.

I cheked in vista and the space is there.  in Ubuntu:Disk usage manager, i find that there is 43.4Gb HD, of which 31.7GB used, leaving 11.7 GB available.    i hadnt checked this before because i didnt know about it....
I then try to use update manager,and get the SAME error!  only 300or so MB available.  btw, in the inital post that said 120Tb, thqat t wasnot a typo i can assure you.  

by the way, aint ubuntu great.  i first tried linux a few years back and couldnt get anywhere, now its a dream, and my vista which is up to date but running sick for unknown reasons is a nightmare .  

keep up the good work. 
but i still have no way to update 10.04 or get to 10.10.   i onlty need t o download 260MB install&.

---

### Post by KAc on 2011-01-14
screen shots...

---

### Post by KAc on 2011-01-14
ok 500 MB or so.  
and i tried computer janitor, no joy.
("Did not find anything to clean up.  You can close the program now. Ok.")

then i tried the terminal (command line, or 'Run') which is under applications accesories.  sudo aptitude clean returnd:
[INDENT][INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

[/INDENT][/INDENT]Then i tried update manager again only to get the same meassage when i try to install the multitude of updates:
[INDENT][INDENT]Not enough free disk space

The upgrade needs a total of 519M free space on disk '/'. Please free at least an additional 414M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

[/INDENT][/INDENT]As i mentinoed before, apt-get does nothing but aptitude seems to do something but not what is required....


[INDENT][/INDENT]

---

### Post by Kirboosy on 2011-01-14
Ok...

I'm assuming you installed it via Live CD (booted off Live CD)

Please don't roast me because I'm not an 'expert' on this, but resizing partitions is a pain in the butt. 

If you set Ubuntu to have a 5 Gb. partition even after you deleted files from Vista it still won't help Ubuntu's space issues. 5Gb is the max Ubuntu can take right now. 

The only way to fix it would to reinstall Ubuntu and manually changing the partition table or to use GParted and change it accordingly (Although the GParted way will get messier faster). Since it seems like you don't have much invested in this install I would just recommend reinstalling it. 

Also downloading the newest version of Ubuntu would be good. This might help fix any issues you have found so far.

---

### Post by Kirboosy on 2011-01-14
Gah double post! Deleted

---

### Post by KAc on 2011-01-14
Thanks for that.  You're right i dont have much to lose by doing a new install.  FYI i am using 10.04 becase when i was installing, i wasnt wanting to do a USB or CD install, i just wanted to use my other HD.  I cant be the only person with such a PC, but, it seems, only 10.04 has this capacity.  
And seeing as its only been release in APril 2010 and still can be upgraded to 10.10 then  this shoudl be do-able right? well, i'm not having a go at you,  thanks again for the advice, i just think that this is an eminently solvable problem without having to do a complete  reinstall.
There are so many options on the Ubuntu download pages , it would be ace if someone could draw up a wizard with recommendations of what you should install.... can someone be assigned?  
I'm thinking: input machine specs, language, current system, etc. money availabel to upgrade etc/  
and POW the top recommendation is......10.10 and find myself a blank CD i suppose. or can i run a CDimage off a second HD?  i think i'll go try that. by the way, when will i be able to cut and paste into terminal? anyone?

---

### Post by KAc on 2011-01-14
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)  is the package i installed.  but currently its only 10.04.       has no-one else had this problem with it??? any help on the thread if they have, siva play.

---

### Post by KAc on 2011-01-14
[:guitar:http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")  is the package i installed.  but currently its only 10.04.       has no-one else had this problem with it??? any help on the thread if they have, siva play.

---

