---
title: "Partitioning Drive and Installing Ubuntu"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by owenisred on 2011-12-16
Hello,

Its been a while since I've posted here. I gave up on Ubuntu a long time ago; I was eager to use it, but I just encountered too many problems with it. Recently I was persuaded to try again, I have a windows 7 64 bit laptop, and I stuck Ubuntu onto a USB stick and changed the boot order, and currently I am running Ubuntu from that (everything looks so much nicer and smoother compared to what i remembered). 

Anyway I tried installing Ubuntu from here, however there was no option to install alongside windows. Only to replace windows or to manually partition hard drive. I reduced the size of the win7 partition and now theres 100GB of free space. However when I select this and click install I get:

NO ROOT FILE SYSTEM FOUND
Please correct this from partitioning menu

I am totally unsure how to fix this, any help would be much appreciated :)

Thanks,
Owen.

---

### Post by Basher101 on 2011-12-16
Hello, glad you found your way back to Ubuntu :D

can you run Gparted? it is in your applications of the Live USB you made. Just open it DO NOT CHANGE ANYTHING NOW just make a screenshot and upload it here so i can help you better.

---

### Post by owenisred on 2011-12-16
Heres the picture, thanks for the reply.

(Hope it attached right :P)

---

### Post by Basher101 on 2011-12-16
okay from here on it is quite easy...but first, how much RAM do you have? I need to know if you need a SWAP partition or not.

---

### Post by owenisred on 2011-12-16
4GB of RAM (DDR3 I _think_)

---

### Post by Basher101 on 2011-12-16
I personally never used more RAM with ubuntu than ~ 1.5 GB... i don't know about how you want to use it. If you do not know what SWAP is, in short your unneeded Processes  get dumped there if you have too many applications to free up some RAM (this is good for older computers). 4 GB should be enough to go without a SWAP partition, but it is your call pal. Do you want it or not?

---

### Post by owenisred on 2011-12-16
I guess ill be ok without :) Thanks

---

### Post by Basher101 on 2011-12-16
then this makes the partitioning a bit easier. Now open Gparted again, right click on your Unallocated space (the 98 GB) and choose new. There on the right you must change the type to Extended partition (you already have 4 Primary partitions and cannot add a fith). Once you have the extended partition, below it should appear the same Space (98 GB) also unallocated. Again, right click it and choose New. On the right you should see the Field "Filesystem" and next to it a box. Click the box and choose "ext4". On the top of Gparted you should see an arrow that looks like the enter key. Click it and the changes will be applied. Now you are done with the partitioning.

---

### Post by owenisred on 2011-12-16
Silly question probably, but how do I change type to extended partition? as far as i can see any time I hit new, I just get the error message saying youve got 4 primary partitions - make an extended one. No option to make an extended one :(

---

### Post by Basher101 on 2011-12-16
Do you actually use your HP tools? or do you not ever use them at all?

p.s. forgot to ask...do you have a 64-bit system?

---

### Post by owenisred on 2011-12-16
Yea Windows 7 is 64 bit. Also I have no Idea what HP tools are - so probably no.

---

### Post by Basher101 on 2011-12-16
I once had an HP laptop and never ever used those...
so you can go ahead and delete the HP tools partition and then move the Recovery partition to the end of the hard disk. Also if you want i can do the installation for you (i will give you a link for a remote control program) i had this idea of helping for a longer time if newbies do not understand how to deal with everything. And i won't have to write so many things...you always learn it way faster when something is shown to you how it is done.

If you want me to do the install i will gladly do so (this will spare me alot of writing and explaining) here is a link for the program [http://www.teamviewer.com/download/version_5x/teamviewer_linux_x64.deb](http://www.teamviewer.com/download/version_5x/teamviewer_linux_x64.deb) when installed you can run it. It will display two numbers, your ID (it stays permanent) and a password (it changes every time you open and close the program). Install the program and write me a PM with the numbers. I will then take control of your PC and make the install for you, explainig in a text program what i am doing.

---

### Post by owenisred on 2011-12-16
Ok, ill PM you the ID and pass :)

---

### Post by owenisred on 2011-12-16
Umm installation failed :(

---

### Post by Basher101 on 2011-12-16
> **owenisred said:**
> Umm installation failed :(

>.< did you try again? maybe the 32 bit version of the program will work... link: [http://www.teamviewer.com/download/version_5x/teamviewer_linux.deb](http://www.teamviewer.com/download/version_5x/teamviewer_linux.deb)

---

### Post by Basher101 on 2011-12-16
alright i set up the install for you. Now edit your thread by choosing the Forum tools at the top and mark the thread as [SOLVED]


regards

---

