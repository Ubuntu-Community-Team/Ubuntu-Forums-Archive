---
title: "A PLEA for help with Catalyst 10.6 install"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Dr. Righteous on 2010-06-23
**Hello all.

I'm new to linux in general and so far I am IN LOVE with it.  
My windows machine is a "toy" only now.  :p

Let me preface this by saying I work from home and rely on a "solid work computer" to get my job done. 
That is an old but very reliable Pentium 4 machine.  
1 gig or RAM the video card is a ATI HD2600 256M video card.
I run 2 Acer 1440x900 monitors in extended desk top.  This is necessary so I can view everything at a glance without hunting for what I need to see.  
I'm running Ubuntu 10.4 32bit and it has been a PLEASURE up to this point accept for one things.  The 2D graphics are a bit sluggish.
When the new Catalyst 10.6 driver was release with updated to OpenGL and much improved 2D performance.  
So a bit of Googling and I found several "methods" to install the driver since it isn't in the regular software channel for Ubuntu.  
Well, following what seemed to be the correct procedure I basically hosed my system yesterday.  After much backtracking I was able to get the video working well enough to get my work done.  At this point it doesn't work as well as it did when I attempted to install the 10.6 driver. 
If anyone can help here,  I need a DE FACTO procedure to install the Catalyst 10.6 driver on my system.  I know this will have to be done via command line (I was great with DOS back in the day) but like I said, I'm a newbie with Linux. 
Thanks for the help in advance!

---

### Post by doas777 on 2010-06-23
my advice is to just use the driver in the repos. the problem with installing external drivers, is that they get unlinked with every other update, and have to be reinstalled. I had four boxes running ATI cards (I still much prefer nvidia) that were incompatible with the repo driver in Karmic, so i had to pull it from ATI themselves. I had to reinstall it on all the PCs everyother week or so, and got some rather weird results (X failures, no mouse pointers, etc). 

I am very pleased that the new repo drivers support HD4200's and HD3870's. now when i get an update that unlinks the driver, the updater takes care of it automatically.

the install procedure is:
1) backup
2) download driver
3) cd to the dir that contains the driver
4) issue the command
```
sudo sh ./<downloadedfilename>
```
5) walk through the menu.
6) reboot
7) test

---

### Post by Dr. Righteous on 2010-06-24
> **doas777 said:**
> my advice is to just use the driver in the repos. the problem with installing external drivers, is that they get unlinked with every other update, and have to be reinstalled. I had four boxes running ATI cards (I still much prefer nvidia) that were incompatible with the repo driver in Karmic, so i had to pull it from ATI themselves. I had to reinstall it on all the PCs everyother week or so, and got some rather weird results (X failures, no mouse pointers, etc). 

I am very pleased that the new repo drivers support HD4200's and HD3870's. now when i get an update that unlinks the driver, the updater takes care of it automatically.

the install procedure is:
1) backup
2) download driver
3) cd to the dir that contains the driver
4) issue the command
```
sudo sh ./<downloadedfilename>
```
5) walk through the menu.
6) reboot
7) test

Well, thanks for the reply but that kind of generalized "how to" is what got me into trouble.  
What I need is detailed step by step command line instructions to get this accomplished.  
1. Backup........  HOW?
2. Got driver
3. Driver is in the directory that terminal defaults to.  I see it if I type DIR.  
4, 5, 6, 7.  Did this part. 
The command I used was  **sudo sh ati-driver-installer-10-6-x86.x86_64.run**
 Looked like it installed, didn't work.  OpenGL drivers were not installed.  :confused:

---

### Post by doas777 on 2010-06-24
hmmm. sounds like you did it right. the first step is just generic (and good advice to give anyone prior to making a system modification). I would generally backup my xorg, and any aticonfig files I already had. 

as for opengl, i've never tried to confim that. I always confirm that 'lshw -C Display' shows flglx as the driver. not sure if the standard install will suffice for your needs. sorry i can't be of more help on that score.

---

### Post by dino99 on 2010-06-24
take care with catalyst, many issues, better to use updated driver:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

you can also search "catalyst" into synaptic and install fglrx-amdcccle

---

