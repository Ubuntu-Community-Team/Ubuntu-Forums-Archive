---
title: "ubuntu 12.10 reinstall problem"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by monkitman on 2013-03-18
Hi, so this kinda has a pre-story but its not related to this category so I will leave out the details. What I am trying to do is install ubuntu 12.10 over a 12.10 install that I did over windows 7 because I was trying to get ubuntu working and things were not turning out very well. What my problem is is that after I did the install even though I am about 99% sure I chose the install over option, the first problematic install of ubuntu is still there. I have tried about 4 times now and all with the same result. Not only that but now problems that were not there when I first installed over windows have appeared since, compiz doesn't seem to be working and I do not see anything but my desktop and cursor. This doesn't really bother me to much since I am trying to get a new install anyways. So what I really need help on is getting this ghost of a ubuntu install to die so my other install will load. I do have two hard drives, I installed the original one over HDa, and I may have installed over top of HDb (which had all my media on it :( ) but I dont remember doing it. If anyone has an idea what is happening please let me know, I was having enough trouble as it was with this other problem and I still have to fix that but I can't even do it without getting this all sorted out and I have spent 3 full days trying to work on it and I am further behind then when I started :( 

PS please forgive my writing, if it doesn't make sense, it's past midnight and I have been at this for hours.

---

### Post by dino99 on 2013-03-18
that is a standard way:

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by nibal on 2013-03-18
> **monkitman said:**
> Hi, so this kinda has a pre-story but its not related to this category so I will leave out the details. What I am trying to do is install ubuntu 12.10 over a 12.10 install that I did over windows 7 because I was trying to get ubuntu working and things were not turning out very well. What my problem is is that after I did the install even though I am about 99% sure I chose the install over option, the first problematic install of ubuntu is still there. I have tried about 4 times now and all with the same result. Not only that but now problems that were not there when I first installed over windows have appeared since, compiz doesn't seem to be working and I do not see anything but my desktop and cursor. This doesn't really bother me to much since I am trying to get a new install anyways. So what I really need help on is getting this ghost of a ubuntu install to die so my other install will load. I do have two hard drives, I installed the original one over HDa, and I may have installed over top of HDb (which had all my media on it :( ) but I dont remember doing it. If anyone has an idea what is happening please let me know, I was having enough trouble as it was with this other problem and I still have to fix that but I can't even do it without getting this all sorted out and I have spent 3 full days trying to work on it and I am further behind then when I started :( 

PS please forgive my writing, if it doesn't make sense, it's past midnight and I have been at this for hours.

Initially, did you install Ubuntu from your Windows desktop by running wubi.exe? That is known to be buggy.
It is never a good idea to reinstall/upgrade something over something problematic. Always do a fresh
install. I assume by now that you have your separate Linux & Windows partitions.

Burn a CD with the Ubuntu Image you downloaded. Boot from that image, and when you reach the partitions, 
edit them yourself. Use your exisiting Linux partitions and format them. No way any ghosts will remain after that!;)

HTH,
Nikos

---

### Post by fantab on 2013-03-18
Since you will be doing a new install anyway, may I suggest that you download and burn Ubuntu 13.04 (beta), its quite stable in itself and definitely a hell lot better than 12.10.


Let me see if I understood you correctly:
You have installed Ubuntu 12.10 over Windows by choosing the install option "replace Windows". Then you reinstalled 12.10 over 12.10, right?
How are you trying to install ubuntu, DVD or USB? What application did you use to burn the .iso to the media?


Did you check for any HDD errors? Use your Ubuntu Live-media to boot and use the utility called "Disks" and run SMART test on both HDDs.
Does you machine has UEFI? USE Gparted to determine what Partition table you are using on your HDD.


Give us more info about your Graphics Card...


You can try and recover your Lost DATA, if you have lost any and want to recover it, then you can do so with [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), infact you can do a lot more.

---

### Post by monkitman on 2013-03-19
I took your advice and installed 13.04. After a tiny bit of work I got it to run nicely. It does feel faster and hasn't crashed yet so it should all be good :) I am still not sure what happened though but I did end up installing over my second drive (even though I didn't select it from what I remember.) Anyway I guess the matter is resolved then. Thanks to all those who replied, its nice to know that when you need help there are people who can give support :)

---

