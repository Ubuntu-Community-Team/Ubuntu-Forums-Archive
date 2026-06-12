---
title: "Fomat HDD for use with Ubuntu"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Zorrokan Zenovka on 2008-06-28
I attempted to install Ubuntu onto an old win 98 PC, but when I get to the partitioning process, just after location select, the process only went 46% of the way through.

I read that there may have been an error in the HDD and so I should try to reformat it?

My other working PC is a dual boot Fedora/XP system.

---

### Post by ajgreeny on 2008-06-28
Try using the live CD and run partition editor on that to delete the current partition(s) and make whatever partitions you need for ubuntu.

The best setup is to have about 8GB for /, up to 1GB for swap, and the rest as /home.  Format all three partitions at this stage as ext3, and I think the installer will go smoothly next time.  When it gets to the partitioning point of installing, chose Manual, and allocate the partitions you have already made as I showed above.

---

### Post by Zorrokan Zenovka on 2008-06-28
So far, I've managed to format the HDD via windows by plugging the HDD into my computer and selecting format in 'my computer'.  

Now, I have transfered the Hard Drive to the other pc, connected it and have put the CD in the tray.

I get as far as the options screen
      Start or install ubuntu etc...
And I press F6 and put acpi=off at the begninning of the string and press [enter] with 'Start or Install' highlighted.

It says 'Loading Linux Kernal and then the screen goes dark.  There is a cursor and 'please wait' flashes breifly.

The screen goes dark for a long time.  Sometimes, it makes it as far as a light brown screen with the Ubuntu logo, other times, it just seems to hang there.

---

### Post by Zorrokan Zenovka on 2008-06-28
Actually, I just realised the HDD I'm using is very ancient... only 10G!  Maybe that is why I can not get very far.

---

### Post by Zorrokan Zenovka on 2008-06-28
My system:

Pentium 2
512MB Ram
10 Gig HDD

Ubuntu Version: 7.04

---

### Post by Midwest-Linux on 2008-06-28
While 512 MB is enough with a Live CD, the Pentium II tells me you have between 300 and 500 Mhz speed. You might want to give Xubuntu a thought, it works great on older machines. If you go that route, try the alternate install CD version.

A 10 GB hard drive is certainly large enough to install Ubuntu, I installed Ubuntu on machines with 4 GB or less. 

 If you decide to go with Ubuntu I  would suggest using the alternate install CD version, and make sure your LAN is connected so it can set up the wireless as you go. 

I personally like to use DBan's "Nuke and Boot" to clear the hard drive before I install anything on a older hard drive. Thats no requirement and others might disagree.

 Also maybe your hard drive is on its way out and thats why its giving you these problems? can you try another hard drive? Just a thought.

---

### Post by Zorrokan Zenovka on 2008-07-03
I've sent away for a Kubuntu CD and the Alt version.

---

