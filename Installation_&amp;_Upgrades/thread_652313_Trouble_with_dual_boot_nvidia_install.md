---
title: "Trouble with dual boot nvidia install"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by schlegelt1 on 2007-12-28
I just built a new rig and i'm having a couple issues trying to install gutsy.  I've already installed xp professional, now i want to resize the xp partition and install gutsy into the remaining space.  It's a 250gb western digital HD, running on a system with a new 8800gt 512 (g92 chipset)...now the issues:

1:  I first tried to install from the live cd, but since i have the new nvidia card, i was unsuccessful launching x.  It's a driver issue from what i've read, and the solution was to install using the text based installation cd, then go about the issue with the nvidia drivers.  

2: I then went to install from that cd and all was well until it went to detect my HD.  For some reason my WD 250gb HD wasn't detected.  

questions:  

1.  Does the fact that i installed xp as a full partition of the 250gb drive prevent ubuntu from detecting the HD?  

2.  Should another partitioning program's live cd work?  I'm referring to gparted (I've never used it, but I've just read about it...).  Would i partition what i want, then should the drive be able to be detected?  This is all assuming that the answer to my first question is true.  

3. Is there a way to fix the nvidia issues with the live cd?  When i boot the normal live cd I get to a screen saying that it's running in low graphics mode, then it freezes.  I can get to a terminal prompt by typing alt-f2, but i dont' know what to do from there.  what are the commands to apt-get the correct driver for my vid card?  Is it even supported?   

4.  Does anyone else have any other suggestions on what might be going on? 


I'm sorry for all the questions, but if anyone can help me out it would be much appreciated.

---

### Post by nosscire on 2007-12-28
As far as I know the text based installation process can't read and use NTFS partitons. Easiest way would be to use a real partitioner and make a clean space on the disk (meaning, resizing but not partitioning the empty space).

I think (not sure however) that you can run from the Ubuntu Live CD if you choose "Safe graphics" or something similar in the bootup menu. Atleast that worked on Feisty live CD. Then you can use GParted. Otherwise you can just use any partition manager from within Windows.


Problem is if you are using a serie 8 card from Nvidia, the drivers may not work at all even after install. Some people got it to work, but most couldn't. Worth a try though I suppose...

---

### Post by Tadock on 2007-12-28
You could try the[ alternative CD]("http://mirrors.kernel.org/ubuntu-releases/gutsy/ubuntu-7.10-alternate-i386.iso") to install Ubuntu I had us it to install Ubuntu with my 8600GT.

---

### Post by schlegelt1 on 2007-12-28
Thanks for the quick reply, I'll check out the windoze partitioners and give them a try.  I figured that was what was going on.  Can you recall how others have gotten the new 8 series cards to work?  Is it simply install the latest nvidia drivers and pray it works :)!?!


***edit***

Tadock:  That was what I did, then i ran into the issue with the HD.  I guess i have to repartition from windows then go about installing from the alternative install cd in the space i free up (I referred to it as the text based install in my first post).  How did you go about the driver issues with your vid card though?

---

### Post by Tadock on 2007-12-28
Briefly,what I did was install Ubuntu then use the[ Envy script]("http://albertomilone.com/nvidia_scripts1.html"). Then I rebooted Ubuntu then used the Nvidia-config in the GUI to set my resolution. Let me know how it goes I'll help in anyway I can.

---

### Post by schlegelt1 on 2007-12-28
Will do...i've used envy before, so hopefully it'll work...i'll keep you all posted


btw, thanx again

---

### Post by nosscire on 2007-12-29
It seams to be about 50-50 chanse to get the cards to work. Either it just works with the new drivers, or (as in my case) it won't work at all. Nothing to do but install and see...

Good luck :)

---

