---
title: "New Ubuntu Installation Dapper Drake 6.06.1 - kernel source missing??"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by sah18 on 2006-08-14
100% newbie to linux.  Last night I installed Dapper Drake 6.06.1 from the Desktop CD.  It seemed to go okay (no errors), and it rebooted fine and I was able to log in.  Next, I wanted to get an internet connection up.  I have only a USB wireless adapter (Belkin 802.11G USB F5D7050).  I read a little about using ndiswrapper, so I downloaded it from another machine that does have a network connection, plus I have the drivers from the belkin cd.  I tried to follow the instructions, however, it appears that there needs to be a link to the kernel source files, and it looks like they aren't installed!  Is this possible?  Again, newbie here:
1) How can I tell if the kernel source files are already installed?
2) Were they supposed to be installed during the initial install (does this mean something went wrong)?
3) If they really are not there, since I don't have a network connection yet on this system (a bit of a catch-22), what are the steps I need to take on my windows system that does have a network connection to download them to either a flash drive or cd, and then install them on the ubuntu box?  If I do need to do this, I need very specific, step-by-step instructions on how to do it, as I have no idea at this point!

thanks for listening to my woes! :-({|=

---

### Post by zxee on 2006-08-14
You might want to look at this thread: [http://www.ubuntuforums.org/showthread.php?t=233359&highlight=build-essentials](http://www.ubuntuforums.org/showthread.php?t=233359&highlight=build-essentials)
since it deals with the program you're trying to install-the thread is on a different release-but should be relevent. 
Also build-essentials is on the cd iirc so doing sudo apt-get install build-essentials should ask you to insert your install cd.

---

