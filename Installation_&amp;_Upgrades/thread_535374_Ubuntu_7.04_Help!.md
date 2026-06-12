---
title: "Ubuntu 7.04 Help!"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by SilentStrike on 2007-08-26
Ok guys so im completely new to linux and ubuntu and everything. So last night I downloaded the Ubuntu 7.04 ISO put it on a CD and loaded it as my OS. At first everything came up and loaded fine and I selected "start or install ubuntu" so I clicked that because I wanted to start it just to mess around with it. It loaded and everything and the sound came on but the desktop was black and said the my screen resolution wasn't right and ubuntu couldn't be displayed. So I restarted my computer and go back to the main ubuntu screen and changed my resolution to what it said it should be by pressing f4 and selecting it form the list. Then once again I clicked "start or install ubuntu" and it was loading fine but then the screen came up and it was ALL messed up. I couldn't see anything and it was all screwed up. So i've been messing around and I find the only way I can use ubuntu is to boot it in safe graphics mode. My cousin who showed me ubuntu has 6.06 and has no problems at all so im thinking of going back to that version because he has no problems and it's LTS unless someone can please help me. Thanks in advance.

---

### Post by jimrz on 2007-08-26
> **SilentStrike said:**
> Ok guys so im completely new to linux and ubuntu and everything. So last night I downloaded the Ubuntu 7.04 ISO put it on a CD and loaded it as my OS. At first everything came up and loaded fine and I selected "start or install ubuntu" so I clicked that because I wanted to start it just to mess around with it. It loaded and everything and the sound came on but the desktop was black and said the my screen resolution wasn't right and ubuntu couldn't be displayed. So I restarted my computer and go back to the main ubuntu screen and changed my resolution to what it said it should be by pressing f4 and selecting it form the list. Then once again I clicked "start or install ubuntu" and it was loading fine but then the screen came up and it was ALL messed up. I couldn't see anything and it was all screwed up. So i've been messing around and I find the only way I can use ubuntu is to boot it in safe graphics mode. My cousin who showed me ubuntu has 6.06 and has no problems at all so im thinking of going back to that version because he has no problems and it's LTS unless someone can please help me. Thanks in advance.

you may well encounter the same on 6.06. please post your hardware specs, especially your video card info, so that poeple here can have an idea what steps may be needed to fix the problem.

---

### Post by SilentStrike on 2007-08-26
Nvidia GeForce 6800
2GB RAM
220GB SATA HD
Intel Core Duo 3.0 Ghz Processors

Anything else you need to know?

---

### Post by Pumalite on 2007-08-26
Try Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) Mark box below 'Start Download'

---

### Post by SilentStrike on 2007-08-26
Ok I will try the alternate CD. And btw I booted up 6.06 and had the same problem :(

---

### Post by SilentStrike on 2007-08-26
Bump

---

### Post by Pumalite on 2007-08-26
What happened with the Alternate CD?

---

### Post by SilentStrike on 2007-08-26
Well so far nothing has happened with the alternative install disk. I kind of wanted to just try it out without installing it to see if it would even work and i'm not ognna partition my HD if its not gonna even work.

---

### Post by Pumalite on 2007-08-26
The Alternate CD is not a 'Live CD'. It's an installation CD and I asure you you will have no problems. It was made for people with computers like yours. It's text-mode: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by SilentStrike on 2007-08-26
Ok well my cousin said he accidentialy deleted his Windows OS when he partitioned his HD. Can someone show me some exact directions so I dont screw anything up?

---

### Post by Pumalite on 2007-08-26
XP or Vista? It makes a difference.

---

### Post by SilentStrike on 2007-08-26
Windows XP and I only have 1 HD.

---

### Post by Pumalite on 2007-08-26
Defrag several times, erase all temp files, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), 'shrink' XP partition, and then install.

---

### Post by SilentStrike on 2007-08-26
Ok thanks.

---

### Post by Pumalite on 2007-08-26
You are welcome. Post back with any problems.

---

### Post by merlinus on 2007-08-26
I have a question, Pumalite.  Do you think it is worth setting windows virtual paging to zero before defragging?

I always see a huge block of unmovable system files (green) near the end of my windows partition when defragging, with lots of free space in between.

-merlin

---

### Post by Pumalite on 2007-08-26
I'm all Linux, so, I'm blissfully ignorant.

---

### Post by SilentStrike on 2007-08-26
Hey im going to defrag over night because it will take several hours. But anyways  I was wondering if you think that my screen could be all messed up when I start ubuntu normally because it doesn't recognize my video card drivers or my drivers arent compatible? I do have the latest beta driver for the nvidia geforce cards.

---

### Post by merlinus on 2007-08-26
I use windows for exactly one app that will not run on anything else.

But perhaps we could add the virtual paging thing to our advice for wannbe dualistics....

It certainly will free up more space on their windows partitions, even with vista.

-merlin

---

### Post by Pumalite on 2007-08-26
Let's not cross the bridge before we get there. if it happens; we'll walk you through it.

---

### Post by SilentStrike on 2007-08-26
Well I don't really want to install Ubuntu yet until I get to play around with it on the live cd without having to load in safe graphics mode. Right now im using Envy to install the correct nvidia driver because I think thats my problem.

---

### Post by Pumalite on 2007-08-26
Go ahead, have a blast!. But, where are you going to install the driver? And, where do you have Envy? Ah...6.06 of course.

---

### Post by SilentStrike on 2007-08-26
I got envy but then I realized that the driver wont install because im running it off of the cd. Duh! Im an idiot sometimes. Anyways what do you mean by ...of course 6.06? Well I guess im going to have to do that defrag tonight, then delete, temp files, and install that gnome xp shrink thing.

---

### Post by Pumalite on 2007-08-26
Now you got it!!

---

### Post by SilentStrike on 2007-08-26
Im just scared when I partition some of my HD off that im accidentially gonna get rid of Windows like my cousin did.

---

### Post by Pumalite on 2007-08-26
When I did, I was so happy; I never looked back.

---

### Post by SilentStrike on 2007-08-26
Hah well you didn't want to dual boot like I did. I will ask my cousin how he did it the 2nd time around without deleting his vista and having to do a whole reinstall.

---

### Post by Pumalite on 2007-08-26
You have all the instructions to safely dual boot.

---

### Post by SilentStrike on 2007-08-27
Ok I have defraged, deleted my temp files, and am about to start up Ubuntu and download the XP "shrink" but I want to know exactly what to do when I get to the partition step in the install. How do I partition my hard drive to dual boot safely?

---

### Post by Pumalite on 2007-08-27
Right click on the partition and you will have a menu where 'shrink partition' will appear.

---

### Post by SilentStrike on 2007-08-27
Im not talking about the XP Partion shrink im tlaking about partitioning my hard drive for ubuntu.

---

### Post by Pumalite on 2007-08-27
Once you have shrunk the XP partition, you can partition the new partition as follows: 500 MB for /swap; 10 GB for '/'; the rest for /home.

---

